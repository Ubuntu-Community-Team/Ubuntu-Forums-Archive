---
title: "IBM Sametime Server installation"
date: 2009-04-28
forum: General Help
---

### Post by memor2000 on 2009-04-28
Hi,

I cannot install IBM Sametime Server Standard on Ubuntu 8.0.4.2 server edition (it's a virtual machine).
When I run the command

*./setuplinux.bin*

as root, installation aborted with this message:

[I]This hardware platform is not supported.
Consult Sametime InfoCenter documentation[/I].


I didn't find any information about this error (only about "This OS is not supported").
I installed Domino server 8.0.2FP1 without problems.

Can anyone help me? Any suggestions?

Thanks

---

### Post by memor2000 on 2009-04-30
UPDATE:

I tried with Ubuntu 8.0.4 Desktop Edition (to enable the GUI) by the command:

java -jar setup.jar

but it doesn't work.
Then I tried with Opensuse (10.3 and 11.1) and these are the results:

[OpenSuse 10.3]
- Setup works only by java (java -jar setup.jar).
- using "./setuplinux.bin" or "./setuplinux.bin -console" the error is:

          Initializing Wizard........
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 559: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 1398: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected
./setuplinux.bin: line 319: bc: command not found
./setuplinux.bin: line 537: [: : integer expression expected


[OpenSuse 11.1]
- setup works only with

./setuplinux.bin -console

Others commands don't work:

-   ./setuplinux.bin

libxcb: WARNING! Program tries to unlock a connection without having acquired a lock first, which indicates a programming error.
There will be no further warnings about this issue.
libxcb: WARNING! Program tries to lock an already locked connection, which indicates a programming error.
There will be no further warnings about this issue.
The installer is unable to run in graphical mode. Try running the installer with the -console or -silent flag.

-   java -jar setup.jar

The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
WARNING: could not delete temporary file /tmp/ismp002/4962957
WARNING: could not delete temporary file /tmp/ismp002/8912456


If someone installed Sametime on Ubuntu (server edition is more interesting) without problems, could he give me suggestions?

Thanks

---

### Post by sahabcse on 2012-02-12
I have installed IBM sametime on ubuntu without any issue. Pls follow below url for more info

[IBM sametime installation in Linux]("http://ubuntulinux.co.in/blog/ubuntu/ibm-sametime-installation-in-linux/")

---

