---
title: "make: msgfmt: Command not found!"
date: 2005-09-19
forum: Desktop Environments
---

### Post by daller on 2005-09-19
Hi All,

Trying to install PyWireless from kde-apps.org!

I downloaded the source here:

[http://kde-apps.org/content/show.php?content=28637](http://kde-apps.org/content/show.php?content=28637)

Then I ran "sudo make install", and it gave me this:

----------

madsen@ubuntu:~/28637-PyWireless/PyWireless$ sudo make install
PyWireless version 2.0 by S.ÃaÄlar Onur <caglar@uludag.org.tr>

make: msgfmt: Command not found!
make: *** [install] Fail 127
madsen@ubuntu:~/28637-PyWireless/PyWireless$    

----------

Whats missing?

---

### Post by mkb137 on 2005-11-05
Install the gettext package

---

### Post by ssarkarhyd on 2007-09-02
I have gettext installed. What then?

---

### Post by theonhighgod on 2008-05-22
I was installing ms-sys for unetbootin and got the error:

```
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 127

```

so installed gettext and that fixed the problem, thanks mkb137, (in Ubuntu 8.10 btw)

ssarkarhyd have you installed "build-essential" cause that's essential if your compiling from source ;)

sorry if im patronising you,

---

### Post by James E. Chargin Jr. on 2008-06-03
I'm running 7.10. I'm trying to build a kernel for an embedded system I'm working to develop. This is based on  the Freescale 8315e, using the Ltib tool. When I include the e2fsprogs package in the build, I see the following message during the build:

make[1]: Leaving directory `.../ltib/ltib-mpc8315erdb-20071129/rpm/BUILD/e2fsprogs-1.34/tests/progs'
making all in po
make[1]: Entering directory `.../ltib/ltib-mpc8315erdb-20071129/rpm/BUILD/e2fsprogs-1.34/po'
: -- updaate cs.po e2fsprogs.pot
rm -f cs.gmo && : -c --statistics -o cs.gmo cs.po
mv cannot stat `t-cs.gmo': No such file or directory
make[1]: *** [cs.gma] Error 1

The "rm -f cs.gmo && : -c --statistics..." line comes from a Makefile line that looks like
"rm -f cs.gmo && $(GMSGFMT) -c --statistics..."

I am assuming that $(GMSGFMT) should be replaced with the path to msgfmt, which I understand is supposed to be part of the gettext package. I've re-installed gettext and I have installed build-essential. "which msgfmt" returns nothing; "which gettext" returns /usr/bin/gettext.

Is there something I'm missing here? I expect installation of the gettext package to add msgfmt, but it doesn't seem to. If its not there, where would I find it?

Thanks,
Jim

---

### Post by theonhighgod on 2008-06-04
Im sorry I dont know much about compiling on embedded systems im no expert but google seemed to suggest Try using "configure --with-include-gettext" (google "t-cs.gmo" and you'll see what i mean)

In synaptic (and most package managers) one is able to see all the files that are installed with a certain package (right click on the package and click properties then gp  to the installed files tab) and by checking out get text one finds 

/usr/share/man/man1/msgfmt.1.gz

to be the path,hope that helps at least a little bit:)

---

### Post by James E. Chargin Jr. on 2008-06-06
Thanks for the link. Your lack of work in embedded systems seems not to have hampered your ability to help me out.

It has also been suggested, on the LTIB mailing list (see [http://savannah.nongnu.org/projects/ltib/]("http://savannah.nongnu.org/projects/ltib/")), that I try building with --disable-nls.

Funny, I use google all day long and didn't think to use it to search for possible solutions. I'm still assuming (erroneously) my problems are unique enough that nobody else could possible be seeing the same error condition. Silly!

It turns out that my system has the gettext-base package installed, which includes gettext but not msgfmt. I installed gettext, which does include msgfmt, but the build still fails with the same symptoms. Maybe a somewhat deeper understanding of how the build is supposed to work will show that my problem is not really msgfmt related.

I'll be trying both suggestions soon. I'll post my results here.

Thanks again.

Jim

---

### Post by James E. Chargin Jr. on 2008-06-06
The suggestion of appending --disable-nls to the configure command, provided by Stuart Hughes on the LTIB mailing list, has solved my build problem. Since my problem is solved, I did not attempt the other suggestion of appending --with-include-gettext.

Jim

---

