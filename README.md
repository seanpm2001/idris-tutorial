idris-tutorials
===============

A series of tutorials related to the Idris Programming Language.

## The Tutorials
### Main

This a copy of the main `Idris` tutorial taken from [idris-dev].

## idrislang.sty

`idrislang.sty` is used to type set `idris` code within the tutorials.
To keep things `DRY` this style file has been *hard* linked with the original kept in `idris-dev`.
Normally, this file should live in the your local texmf tree, but if we want auto-generation of PDFs then the style file needs to be distributed alongside...

## Building

Each tutorial is written in `LaTeX` and the build tool `latexmk` will be used to manage the compilation process.
`Emacs` with `AucTeX-mode` is used during writing.
The `auto` generated by `AucTeX` should be taken care of with the `.gitignore`.
Ditto goes with those pesky `.DS_Store` files generated by Mac OS X.
However, do not be surprised to see several `AucTeX` related code in `LaTeX` comments at the bottom of several files.

## Ancillary Stuff

### Bash Aliases

Useful bash aliases are:

    alias latexBuild='latexmk -gg -pdf -pvc -bibtex'
    alias latexQBuild='latexmk -gg -pdf -bibtex'
    alias latexClean='latexmk -c'
    alias latexClobber='latexmk -C'

### LaTeXmk Extra Configuration

Some customisations to `latexmk`.

    $pdf_previewer = "start evince %O %S"; # replace with preview for Mac OS X
    $pdf_update_method = 0;

    $clean_ext .= 'run.xml loe tex.bak acn ist bbl bcf fdb_latexmk glo run nav snm %R-blx.bib';

    add_cus_dep('glo', 'gls', 0, 'makeglossaries');
    add_cus_dep('acn', 'acr', 0, 'makeglossaries');
    add_cus_dep('cto', 'cti', 0, 'makeglossaries');
    add_cus_dep('mto', 'mti', 0, 'makeglossaries');
     
    push @generated_exts, 'glo', 'gls', 'glg';
    push @generated_exts, 'acn', 'acr', 'alg';
    push @generated_exts, 'cto', 'cti';
    push @generated_exts, 'mto', 'mti';
     
    $clean_ext .= ' %R.ist %R.xdy';
     
    sub makeglossaries {
     if ( $silent ) {
        system "makeglossaries -q '$_[0]'";
      }
      else {
        system "makeglossaries '$_[0]'";
      };
    }


## Auxuliary Stuff

Other useful tooling I use include:

### Style.check.rb

The tool [style-check.rb](http://www.cs.umd.edu/~nspring/software/style-check-readme.html) is a programmer friendly tool to parse `LaTeX` files for *ambiguous or verbose prose* [sic] as dictated by the program's author and more importantly well-known sources for scientific (and normal) writing. Such as: the [Day and Gaestal book](http://www.cambridge.org/gb/academic/subjects/general-science/science-handbooks/how-write-and-publish-scientific-paper-7th-edition).


