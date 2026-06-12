---
title: "VIM 256 Color Support Config Xdefaults - Ubuntu 12.04"
date: 2012-06-27
forum: Desktop Environments
---

### Post by airper on 2012-06-27
Hi,

I'm trying to get a start with VIM, so I'm following Derek Wyatt's video tutorials. However I can't get colorschemes working in VIM for syntax highlighting. 

Clearly I'm doing something wrong,  or are too dumb to use VIM (The latter is a real possibility)!!!

I've figured out that Xterm is only running in 8 color mode, not 256 colors, so I found this HowTo which I've attempted to follow to get 256 colors working.

[http://push.cx/2008/256-color-xterms-in-ubuntu](http://push.cx/2008/256-color-xterms-in-ubuntu)

But even though I've installed  [FONT=monospace]'[/FONT]ncurses-term' I don't have an Xdefault file or 'vimrc' as far as I can see.

 ~/.Xdefaults and ~/.vimrc  report no files or directory.

If I run 
$ tput colors

I get a response of 8

[COLOR=Black]If I run 

[COLOR=#000066]$ echo[/COLOR] [/COLOR][COLOR=#0000FF][COLOR=Black]$TERM

I get xterm

It should be [/COLOR][/COLOR]'xterm-256color[COLOR=#0000ff][COLOR=Black]'

I'm stuck now, can anyone help?


[/COLOR]
[/COLOR]

---

### Post by airper on 2012-06-27
Okay,

You have to manually create the:

[COLOR=Black].Xdefaults
.vimrc
.xsession[/COLOR]

files in your home directory. I did that and then edited them with:

Xdefaults
```
*customization: -color

Xterm*termName: xterm-256color
```xsession
```
if [ -f $HOME/.Xdefaults ]; 

then   xrdb -merge $HOME/.Xdefaults 

fi


```But I'm still getting

$ tput colors [COLOR=#cc66cc]

8[/COLOR] 

$ [COLOR=#000066]echo[/COLOR] [COLOR=#0000ff]$TERM[/COLOR] 

xterm

So, stuck again?

---

### Post by itcotbtoemik on 2012-06-27
> **airper said:**
> Okay,
```
*customization: -color

Xterm*termName: xterm-256color
```

The class name is "XTerm", not "Xterm".

---

### Post by airper on 2012-06-28
Thanks and well spotted, but that still hasn't fixed the color system, I'm still in 8 color mode.

The answer it out there somewhere.

---

### Post by itcotbtoemik on 2012-06-28
> **airper said:**
> Thanks and well spotted, but that still hasn't fixed the color system, I'm still in 8 color mode.

The answer it out there somewhere.

Is $TERM still "xterm"?

---

### Post by airper on 2012-06-28
Hi,

Yes, output from echo $TERM remain xterm and tput colors is 8

Of course what I'm trying to do here is get VIM to run with the Desert color scheme, it obviously won't do that until XTerm is running in 256 color mode.

As always with these little problems learning a lot though. 

the more I read and understand about VIM the more I see how powerful it is. I can understand why people spend the time and effort learning to use it properly, really awesome software.

---

### Post by itcotbtoemik on 2012-06-28
> **airper said:**
> Hi,

Yes, output from echo $TERM remain xterm and tput colors is 8


Probably your terminal database does not have xterm-256color then:
> 
This option specifies the name of the terminal type to be set in the TERM environment variable. It corresponds to the **termName** resource. This terminal type must exist in the terminal database (termcap or terminfo, depending on how *xterm* is built) and should have *li#* and *co#* entries. If the terminal type is not found, *xterm* uses the built-in list “xterm”, “vt102”, etc.


---

### Post by airper on 2012-06-29
If I run;

find /lib/terminfo /usr/share/terminfo -name "*256*"

I get this list, so I'm assuming here I've got xterm-256color loaded okay?


```
/lib/terminfo/x/xterm-256color
/lib/terminfo/s/screen-256color
/lib/terminfo/s/screen-256color-bce
/usr/share/terminfo/x/xnuppc+256x96
/usr/share/terminfo/x/xnuppc-256x96-m
/usr/share/terminfo/x/xnuppc-256x96
/usr/share/terminfo/x/xterm+256color
/usr/share/terminfo/s/screen-256color-bce-s
/usr/share/terminfo/s/screen-256color-s
/usr/share/terminfo/d/darwin-256x96
/usr/share/terminfo/d/darwin-256x96-m
/usr/share/terminfo/g/gnome-256color
/usr/share/terminfo/p/putty-256color
/usr/share/terminfo/m/mlterm-256color
/usr/share/terminfo/m/mrxvt-256color
/usr/share/terminfo/r/rxvt-256color
/usr/share/terminfo/r/rxvt-unicode-256color
/usr/share/terminfo/v/vte-256color
/usr/share/terminfo/E/Eterm-256color
/usr/share/terminfo/k/konsole-256color

```

---

### Post by miggys on 2012-06-29
Are you able to set it manually?

export TERM=xterm-256color

If that worked then your current xterm should have $TERM of xterm-256color.
You don't want to do this all the time, but this is just to find out where the issue is...

If that works, does manually loading your resources file work?  ie open a new xterm and run this:

xrdb -merge ~/.Xdefaults

now during this session, all newly started xterms should have xterm-256color.  If that worked then probably ubuntu is not sourcing .xsession on log-in.  Maybe you can make .xsession autorun on start up?

---

### Post by itcotbtoemik on 2012-06-29
> **miggys said:**
> Are you able to set it manually?

export TERM=xterm-256color


Actually ```
infocmp xterm-256color
``` is a more direct way of checking if the
description exists (for most systems - there are still some that use termcap).

The hint about .xsession sounds plausible - I generally don't use xrdb
but rely upon setting $XAPPLRESDIR for private resource settings.

---

### Post by airper on 2012-06-30
Thanks Guys,

Got it working .xsession was not loading so made it run on start, that fixed the problem.

Excellent help as always here.

Best Regards

Wayne

---

### Post by pixel67 on 2013-04-10
I  was able to get 256colors working and set solarized as the colorscheme, thanks for the help.
Let me know if you are still having issues I will give you step by step instructions ;)

I just noticed that you did get it working, excellent. It's important to have a your environment set up the way you like.
So if anyone needs step by step just post a reply and I will be more than happy to post the instructions.
I just set up 2 Ubuntu servers on a VPS, learning linux is liberating!

---

