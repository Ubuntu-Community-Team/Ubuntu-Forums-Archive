---
title: "Deadkeys not working on KDE 4.4 from Kubuntu PPA"
date: 2010-02-11
forum: Desktop Environments
---

### Post by vitorsouza on 2010-02-11
Hello all,

I've recently updated KDE 4.4 using Kubuntu PPA. I was already using the version RC1 and today I updated to a more recent version that was made available in the PPA repository.

After the update, deadkeys won't work on KDE applications and Skype. Other non-KDE application work fine. Is anyone else experiencing this issue?

I created a bug report for kubuntu-ppa here:

[https://bugs.launchpad.net/kubuntu-ppa/+bug/520408](https://bugs.launchpad.net/kubuntu-ppa/+bug/520408)

If anyone knows a workaround, please let me know.

Thanks,

Vítor Souza

---

### Post by Zorael on 2010-02-11
As of 4.4, ibus has been set to be the default input method engine (IME) in Kubuntu (and Ubuntu as of 9.10). It allows input of complex characters, such as Chinese, Japanese, Korean, etc. One of its known bugs is that its XIM module can't handle dead keys, which I reported upstream back in September ([link](http://code.google.com/p/ibus/issues/detail?id=526)). No fix.

Basically, for input apps can either rely on XIM (standard X input module), GTK or Qt. Input methods supply their own modules for these, hijacks the input and returns it with whatever you've set it up to accept input as (eg. Japanese). It's also possible for apps to just hijack keyboard strokes directly, I guess.

Anyway, the point is that different apps rely on different modules to catch input, with GNOME apps generally relying on the GTK module, and KDE apps on the Qt module. Notably, OpenOffice.org uses the GTK module if the GNOME compatibility package is installed, and otherwise XIM. Apps that obviously don't belong to neither of the camps (GTK/Qt) usually rely on XIM, like xterm.

**edit**: If you don't need to be able to input any special characters, you can disable the input method entirely.
```
$ sudo im-switch -s none
```

-------------------------------------------------------------------------
(pre-edit)

The workaround is to tell your XIM apps *not* to use the XIM wrapper of ibus. The easiest way is to create a script for each of your apps that don't work. For example, to launch Skype (comments in italic);
```
#!/bin/bash

unset XMODIFIERS    *# unsets the environment variable telling apps which XIM module to use*
/usr/bin/skype &    *# starts Skype in a child process*
**disown** %1            *# disowns the child process so as not to cause potential issues if run from a terminal*
```
Save it in **/usr/local/bin** or **~/bin** (or anywhere, preferably somewhere in your PATH), and edit your menu entries to point them there.

Using the absolute path (**/usr/bin/*executable***) might be a good idea, as if you save it somewhere in your path with the same filename as the executable has (eg. **/usr/local/bin/skype**), it will run itself as a background process and infinitely loop until the script file is renamed or deleted.

---

### Post by vitorsouza on 2010-02-11
Hi Zorael,

Thanks for the reply and especially for the explanation. However, I find the following problems:

[LIST]
[*]There is no ibus process running if I do a ps aux | grep ibus;
[*]I checked on dselect and the package ibus is not installed;
[*]The XMODIFIERS variable contains nothing if I do echo $XMODIFIERS
[*]The executable script that you suggested didn't work for me, then. And also said: "line 5: unset: `%1': not a valid identifier"
[/LIST]

I'll try and install ibus to see if that is what's missing. I'll post again if it works.

When you say "if I don't need no special character", what is considered a special character? I don't need any Japanese, Chinese or Cyrillic, but I do use accented letters (á, ã, à, â, ä, ç) and some symbols (e.g.: &#8364;). Anyways, I'll try the im-switch thing too.

Thanks again,
Vítor Souza


**Edit 01:**

It seems like I'm still using XIM for everyone:

$ ls -la /etc/X11/xinit/xinput.d/all_ALL
lrwxrwxrwx 1 root root 32 2010-02-11 13:52 /etc/X11/xinit/xinput.d/all_ALL -> /etc/alternatives/xinput-all_ALL

$ ls -la /etc/alternatives/xinput-all_ALL
lrwxrwxrwx 1 root root 35 2010-02-11 13:52 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default-xim

$ cat /etc/X11/xinit/xinput.d/default-xim                               
#
# General configuration to set X Input Method (xim) for GTK and QT.
# See im-switch(8) and /usr/share/doc/im-switch/README.Debian .

#
# Define IM for traditional X application with XIM
#
#  XIM server name
#  XIM program /path/filename
#  XIM program command line arguments
#  XMODIFIERS environment parameter
#
XIM=none
XIM_PROGRAM=
XIM_ARGS=

#
# Define GTK and QT IM module
#   They may or may not be using xim as the IM.
#
GTK_IM_MODULE=xim
QT_IM_MODULE=xim

#
# Define lists of packages neded for above IM to function
#
DEPENDS=

#
# Define X start up hook script to update IM environment
#

---

### Post by vitorsouza on 2010-02-11
I issued the command:

sudo im-switch -s none

And at first it didn't do anything. Then I installed ibus:

sudo apt-get install ibus

And restarted the computer. Now it's working again, but I'm not sure what fixed it, because of this:

$ echo $XMODIFIERS
@im=none

Before, the XMODIFIERS variable was empty. Now it has that. The configuration files are still the same:

$ ls -la /etc/X11/xinit/xinput.d/all_ALL
lrwxrwxrwx 1 root root 32 2010-02-11 13:52 /etc/X11/xinit/xinput.d/all_ALL -> /etc/alternatives/xinput-all_ALL

$ ls -la /etc/alternatives/xinput-all_ALL
lrwxrwxrwx 1 root root 35 2010-02-11 13:52 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default-xim

Go figure...

Anyways, thanks for the help! Hope this can help other people too...

Vítor Souza

---

### Post by Zorael on 2010-02-11
Regarding the script error, my bad; that's supposed to be **disown**, not **unset**.

Regarding ibus not present; curious. In that case this may just be unrelated to the bug I know of.

Could you post the output of the following?
```
$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
$ im-switch -l
```

By "special character" I just mean complex characters, where you enter syllables, pick a candidate and commit to text; basically CJK, Chinese-Japanese-Korean. &#12394;&#12395;&#12396;&#12397;&#12398;, &#39640;&#25152;&#24656;&#24598;&#30151; and the like. Bad wording on my part.


**edit**: Well, if it works that's always good. It's not a perfect solution though, as now you could potentially be needlessly running the ibus daemon, wasting a few megs of memory on something you won't use. 'ps aux | grep ibus' should tell you.

**edit 2**: No, I guess that if XMODIFIERS has @im=none that probably means the input method alternative is properly set as none, and ibus isn't running. Joy!

(a post ripens with each edit)

---

### Post by vitorsouza on 2010-02-11
Here it goes:

$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
GTK: xim, Qt: xim, XMOD: @im=none

$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
No private "/home/vitor/.xinput.d/en_US or /home/vitor/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
 link currently points to default-xim
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
/usr/bin/find: `/home/vitor/.xinput.d': No such file or directory
default default-xim ibus ibus-kde none th-xim
=======================================================

And here's the default file, with comments removed:
$ cat /etc/X11/xinit/xinput.d/default
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
GTK_IM_MODULE=
QT_IM_MODULE=
DEPENDS=


And the none file:

$ cat /etc/X11/xinit/xinput.d/none
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
GTK_IM_MODULE=
QT_IM_MODULE=
XMODIFIERS=
DEPENDS=

---

### Post by Zorael on 2010-02-11
```
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
link currently points to **default-xim**
```
So the file it's using is **/etc/X11/xinit/xinput.d/default-xim** (and not **default**).

Unsure as to why an empty XMODIFIERS would exhibit different behavior compared to when containing **@im=none**, but I don't really know the inner workings.

You could try to force an empty XMODIFIERS and see if the behavior returns, just to sate curiosity.
```
$ unset XMODIFIERS; /usr/bin/skype &
```

---

### Post by vitorsouza on 2010-02-11
I ran it just like you said:

unset XMODIFIERS; /usr/bin/skype &

And the problem did not return. Deadkeys were working normally.

Vítor

---

### Post by Zorael on 2010-02-11
Well, if there's anything I hate just as much as problems that can't be solved, it's problems that solve themselves (for no apparent reason). Okay, slightly less.

---

### Post by svsummer on 2010-02-11
I had the same problem and succeeded in fixing it by repeating steps above. Note, however, that "sudo im-switch -s none" does not work; you need to set it to  "sudo im-switch -s default-xim".

Actually, I removed imbus (and its automatically installed dependencies) after deadkeys worked again, and deadkeys have continued to work. So, my guess is that it is only the configuration files that are inadequately set when installing KDE 4.4 from ppa, and that it would suffice to call "sudo im-switch -s default-xim" to fix things.

In any case, thans for all the helpfull points, I really need the deadkeys to work :)

---

### Post by xvila on 2010-02-11
Thanks to all of you !!
I have had a terrible day trying to fix this
I agree with svsummer

"sudo im-switch -s default-xim"

does the trick

Other than that, KDE 4.4 works perfectly on my macbook ! What a good work !

---

### Post by vitorsouza on 2010-02-11
Now that you said that, I do remember setting it not only to none but also to other options. I guess the last one I tried was default-xim, then.

Well, now we have a confirmation on the workaround. Just do:

sudo im-switch -s default-xim

Thanks!
Vítor

---

### Post by piousp on 2010-02-12
I have the same problem with those dead keys :(

Output of echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS

```
GTK: , Qt: , XMOD:
```

Output of im-switch -l
```
Your input method setup under es_CR locale as below.
=======================================================
No private "/home/piousp/.xinput.d/es_CR or /home/piousp/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - modo manual
 el enlace apunta actualmente a none
default - prioridad 10
default-xim - prioridad 0
none - prioridad 0
Actualmente la «mejor» versión es default.
=======================================================
The available input method configuration files are:
/usr/bin/find: «/home/piousp/.xinput.d»: No existe el fichero ó directorio
default default-xim ibus-kde none th-xim
=======================================================
```

So, i just entered ```
sudo im-switch -s default-xim
``` and its not working, i still get ´o instead of ó.
I'm gonna restart to see if it needs to.

**EDIT:**

I can confirm that
```
sudo im-switch -s default-xim
```
does the trick!

THANKS A LOT!

---

### Post by syncmasterpt on 2010-02-12
The sudo im-switch -s default-xim command and restarting KDM solved the issue for me....

I was going nuts with it....:popcorn:

---

### Post by orestesmas on 2010-02-17
Same from me here. I simply did a "sudo im-switch -s default-xim" and then back again to "sudo im-switch -s default", with no new packages installed/removed, and this solved the issue for me.

Sometimes I wonder how you guys manage to master such obscure things...

---

