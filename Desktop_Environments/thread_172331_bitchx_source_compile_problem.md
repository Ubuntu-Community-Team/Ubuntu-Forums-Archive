---
title: "bitchx source compile problem"
date: 2006-05-08
forum: Desktop Environments
---

### Post by mikekc on 2006-05-08
I can't seem to get bitchx to compile from the source I know there is a package via apt-get but that package doesn't have proxy support because I am wanting to be able to use tor.  Right now I am just using binaries but the binaries don't have any of bitchx's main files.  Here is the compiling error.

---------------------------------------------------------------------------
ctcp.c:179: error: static declaration of âctcp_typeâ follows non-static declaration
/home/acid/BitchX/include/ctcp.h:59: error: previous declaration of âctcp_typeâ was here
ctcp.c: In function âdo_versionâ:
ctcp.c:896: warning: pointer targets in passing argument 1 of âstripansicodesâ differ in signedness
ctcp.c: In function âdo_notice_ctcpâ:
ctcp.c:1367: warning: pointer targets in passing argument 1 of âstripansiâ differ in signedness
make[1]: *** [ctcp.o] Error 1
make[1]: Leaving directory `/home/acid/BitchX/source'
make: *** [BitchX] Error 2
-----------------------------------------------------------------------
I have no idea what I have to install to get this to compile I've already installed the compiler packages and ncurses and all of that.  It is very odd.  Please let me know what I can do.

---

### Post by Ramses de Norre on 2006-05-08
Hmm I don't talk your language.. Could you translate it? And are there any errors when running ./configure?

---

### Post by mikekc on 2006-05-08
[QUOTE=Ramses de Norre]Hmm I don't talk your language.. Could you translate it? And are there any errors when running ./configure?[/QUOTE]
hmm nope I didn't notice any errors on the configure, it is odd.

---

