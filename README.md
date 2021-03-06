# vim-perl-testing

A set of utilities to help you write and run your perl tests directly
from your favorite editor.

## Available commands..

you might want to map to handy keystrokes:

```
:call GotoCorresponding( <open_with:tabnew|split|..[default=edit]> )
```

If you are currently editing a module, this function will open the
corresponding .t file. If you are currently editing a test
file, it will open the corresponding module. Of course,
this requires you to have a correspondance of tests and modules in the
first place.

If the corresponding file is already open, it will bring you to the right buffer.

See http://blogs.perl.org/users/ovid/2013/03/discoverable-tests-and-creating-testing-standards.html
for the details of this and also to learn about the inspiration for this
plugin.

```
:call RunTestForCurrentSub()
```

When working on a subroutine, you may feel like running the corresponding
test. The function will find your corresponding test file and will try to 
run the subroutine in that test file that is supposed to test the subroutine
you are currently changing.

To execute only a given subroutine from your testfile you should add something like
the following after your "use"-statements:
```
if ( $ARGV[ 0 ] ) {
    no strict 'refs';
    &{$ARGV[ 0 ]}();
    done_testing;
exit 0;
```

## TESTING THE PLUGIN

This plugin comes with a set of unit tests. To run the tests, you need to
install another vim plugin: vim-unittest. It is available on github:
https://github.com/h1mesuke/vim-unittest

With vim-unittest installed, cd to the directory where you installed
vim-perl-testing to and open a vim instance with one of the file in the
test/ directory. Then simply run :UnitTest

## LICENSE

See `:help license`.
