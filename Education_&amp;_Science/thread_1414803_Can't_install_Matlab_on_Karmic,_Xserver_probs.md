---
title: "Can't install Matlab on Karmic, Xserver probs"
date: 2010-02-24
forum: Education &amp; Science
---

### Post by ngover on 2010-02-24
Hi all,

I'm trying to install Matlab R2007a on Karmic with no joy.  I've searched and searched but can't find anyone with the same issue, so here goes...

I try to install from the cdrom location by going:
./install_unix.sh

and I get back:
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/unix/update/install/main.sh: 168: /media/cdrom0/unix/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .


Well... it's nothing if not polite.  So I try the -t install and get straight to the Software License Agreement, which I accept and subsequently terminal tells me

/media/cdrom0/unix/update/install/main.sh: 582: /media/cdrom0/unix/update/bin/glnxa64/xsetup: not found

WTF Matlab?!  So using the GUI I follow the filepath and find that the disc only has:
/media/cdrom0/unix/update/glnx86
Which is why I can't find it.  Der.  I'm running 64bit Karmic which (and I do suck at understanding kompooters) seems to be my problem.... and uni starts next week.

HELP!

---

### Post by texaswriter on 2010-02-24
```
sudo aptitude install octave qtoctave

```

Octave works just like it... scripts, functions, etc. 

You can use it command line: octave or qtoctave for a gui experience. 

good luck

---

### Post by ssam on 2010-02-24
have you tried the instructions in the ubuntu docs?
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by ngover on 2010-02-24
@texaswr: I've got Octave running as a backup, however getting Matlab running is still my goal and plugging through errors like this is a good learning tool for me

@ssam: Yes.  All of them.  And all the forums on the Mathworks site.  I think I broke the internets looking for stuff.

---

### Post by ngover on 2010-02-24
Update:  I'm getting through this slowly, however I've needed to create a symbolic link so the 32bit programme can run on the 64bit machine.

HOWEVER, I am being told that the link is broken.  "This link cannot be used, because its target "usr/local/matlab_sv/sys/java/jre/glnx86" doesn't exist.  But it does, and gln86 is a folder.  WTF?

---

### Post by sprince09 on 2010-02-28
Are you sure that MATLAB 32bit can be installed on a 64bit system?

Also, make sure you're installing as root:

```

sudo sh install_unix.sh

```

I remember having had similar problems during MATLAB installations in the past and I'm 99% sure it ended up being that I wasn't installing as root :neutral:

---

### Post by ngover on 2010-03-02
Problem solved.  I found the JRE I was operating with was a newer version than Matlab '07 recognised, so it simply took a few (5) symbolic links strategically placed to ensure the filepaths all matched up.

@sprince09: So yeah, 32bit Matlab can go on a 64bit machine.  There's a bit of support on the Mathworks site for installation, the main 'issue' is instead of saying "install_unix.sh" you need to force the mismatched install by going "install_unix.sh -glnx86"; and you're right, you need to be sudo too.

---

### Post by Rohan on 2010-03-04
Can't tell you how many time I've had that problem with software 0 especially java.

Can you tell me what links you made because I am trying to do the same install.

---

