---
title: "problem with Auto07p-software for continiation and bifurcation analysis"
date: 2011-12-30
forum: Education &amp; Science
---

### Post by j.siahboomi on 2011-12-30
Dear all.

I need to use Auto(a software for continuation and bifurcation analysis) and i've chosen Auto07p. I downloaded it and extracted the tar file on the Desktop.then type './configure' and 'make' and 'make install'.when i want to run auto and i use command auto,nothing occured.
after that i edited auto/07p/cmds/auto.env.sh and auto/07p/cmds/auto.env. 
in auto.env :


setenv AUTO_DIR $Desktop/auto/07p
set    path=($AUTO_DIR/cmds $AUTO_DIR/bin  $path)

and in the auto.env.sh:

AUTO_DIR=$Desktop/auto/07p
PATH=$AUTO_DIR/cmds:$AUTO_DIR/bin:$PATH

then i used command:

source cmds/auto.env
or
source cmds/auto.env.sh

for "auto.env.sh" there in no error or message.
for "auto.env" this error occured:

No command 'setenv' found, did you mean:
 Command 'netenv' from package 'netenv' (universe)
setenv: command not found
bash: cmds/auto.env: line 5: syntax error near unexpected token `('
bash: cmds/auto.env: line 5: `set    path=($AUTO_DIR/cmds $AUTO_DIR/bin  $path)'

i use UBUNTU 11.04.
what should i do for that? please give me some tips.

---

### Post by jdelgado on 2012-01-19
Hi,

I am having the same problem with installing grads. 

"no command setenv found"

---

### Post by jdelgado on 2012-01-19
this was a good help:

[http://forums.devshed.com/unix-help-35/bash-setenv-command-not-found-184593.html](http://forums.devshed.com/unix-help-35/bash-setenv-command-not-found-184593.html)

use env XXX=/whatever/ instead of setenv XXX /whatever/

---

