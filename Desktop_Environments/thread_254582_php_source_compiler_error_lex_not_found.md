---
title: "php source compiler error: lex not found"
date: 2006-09-10
forum: Desktop Environments
---

### Post by baosheng on 2006-09-10
root@orioleQ:/home/forrest/install/php-4.4.4# ./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql
loading cache ./config.cache
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... exit 0;
checking whether ln -s works... yes
checking for gawk... no
checking for mawk... mawk
checking for bison... no
checking for byacc... no
configure: warning: You will need bison if you want to regenerate the PHP parsers.
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2540: lex: command not found
configure: error: cannot find output from lex; giving up

---

### Post by tuxinvader on 2006-09-10
In a terminal run "sudo apt-get install flex" and try again

---

