---
title: "Login problem (gnome-session)"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Emphii on 2006-06-15
Hello everyone.

First of all: Machine, I run/write this, is HP i2000/IA-64 (early ones, I guess).

I have had problem to login to Gnome. It also means Failsafe Gnome.
This means new users too. And it is from the first install (only oem-user
had succesful desktop login just as long as it was needed).
Now I'm logged in via Failsafe Xsession.

After, I checked couple of hints from forums and from google, I started to
run programs one by one.

My .xsession-errors looks like this:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "xxxxxxxxxxxxxx"
/etc/gdm/Xsession: Beginning session setup...

No clue from there..

Well there seems to be problem with gnome-session. As it gives
Segmentation Fault, when running by hand.

Here's gzipped strace, if someone understand where it is going to woods.
[ATTACH]11263[/ATTACH]

Any help would be appreciated.

---

### Post by ayoli on 2006-06-15
you may try to remove your gconf and gnome hidden dirs by type in a terminal:

rm -rf .gconf*
rm -rf .gnome*

cheers

---

### Post by ifokkema on 2006-06-15
[QUOTE=ayoli]you may try to remove your gconf and gnome hidden dirs by type in a terminal:

rm -rf .gconf*
rm -rf .gnome*

cheers[/QUOTE]

I think he means new users have this, too. That would mean that this is a system-wide thing.

When did the problem start? Right after you installed the system from the CD? Or did you upgrade from Breezy?

---

### Post by ayoli on 2006-06-15
oops right, seems i've read to quickly ;)

---

### Post by Emphii on 2006-06-16
> ifokkema
When did the problem start? Right after you installed the system from the CD? Or did you upgrade from Breezy?

Right after fresh install. There seems to be gnome-session update available, so I'll give it a try.

---

### Post by Emphii on 2006-06-16
Right. Update was as bad, as earlier. Well I mounted another disk, which has Debian sarge, and copied gnome-session from there. It's version 2.8.1, while this new one is 2.14.2 (or similar).
Well, now I can login.

I think, I'll try once more install this whole system, this time I'll restirct installation packages to stable only. Just to get sure/test.. =)

BTW. If someone is trying this IA-64 installation, I read somewhere, that HPPA-install cd is broken someway. So is IA-64 too. Do a network install (dl mini.iso). And kernel-image n.n.n.n.n does not work (at least not in i2000), but n.n.n.n.n-smp does.

---

### Post by flowtron on 2006-09-10
I had this problem too,
it started after I did some stuff to my configs to enable my nvidia gfx-card.
While testing I had a hard freeze of the whole system - after that I also got the mentioned issue.

Only failsafe session available under Gnome.

All forum posts I found so far did not help, the #ubuntu channel is full of newbies and nobody could help me there either.

In the end I hacked my /etc/gdm/Xsession script to manually start gnome-session.
I also check for the parameter passed not being "default" (since I switched in /usr/share/gdm/BuiltInSessions/default.desktop from Exec=default to Exec=custom) and in case I do get "default" passed as param then not running the failsafe call.

```
if [ "x$command" = "xcustom" ] ; then
  #flowtron : 20060910 - try to fix non-running "gnome-session"
  # w/o checking for "default" below this will run "failsafe" upon shutdown!
  gnome-session
  shift
  set default $*
fi

```

and

```
echo "$0: Executing $command failed, will try to run x-terminal-emulator"

# flowtron : 20060910 - try to fix non-running "gnome-session" but keep it from running "failsafe" on shutdown
if [ "$*" = "default" ]
then
  echo "not rerunning [flowtron]"
else

if [ -n "$zenity" ] ; then
        "$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner. ALL PARAMS = $*"`"
fi

exec x-terminal-emulator -geometry 80x24+0+0
fi
```

I still want to investigate further into this since this is obviously an evil hack, but maybe it'll help others along the way and also might get me some response from someone knowledgeable :)

---

### Post by flowtron on 2006-12-16
Since the updates I ran yesterday I'm experiencing the same problem again. :-k 

Since no further replies have cropped up here and there was no warning at any time the installation overwrote some files I had manually modified I am now finally convinced Ubuntu is _not_ the distro of *my* choice.
](*,) 
Too bad - but there you have it ... I went to linux because I was so frustrated with a system trying to tell me it knows better ... and obviously failing in the process.
So I'll either go back to the good old stable Debian (Sarge) or go with unstable and be really careful about updating ... but with Ubuntu I thought I could rely on the updates ... ahhh, well - everybody else : enjoy it while it lasts! :cool: 

Oh, BTW:
Never touch a running system!
;-)

---

### Post by ifokkema on 2006-12-18
Hmm.... since it's a config file you modified, during the upgrade it should ask you what you want to do: overwrite it, or keep it. Then again, that's when you upgrade through the console. I'm not sure what the update-manager will do... ;)

---

### Post by flowtron on 2006-12-18
Yeah - well with stable debian (Woody or Sarge) I always used to get a warning about detected human-intervention (read : modified files from original installation) and the choice to keep/discard/backup my version prior to continuing ... no matter wether going via console or a graphical package managment. They run the same stuff in the end anyway - should be so with Ubuntu too - but probably some switches get passed when using synaptic that tell it to assume the user is a dummy.
---omitted further ranting---

---

### Post by flowtron on 2006-12-29
... found some time to tinker with the default sessions properties and I now also start gnome-session for a default session in my modified version of /etc/gdm/Xsession ... seems to be running again - now to find out what driver issues the kernel update brought to sprawl XMMS ... but VLC can play the few M3Us I sometimes run from PC too, so that's not really a pressing problem ;-)

Sorry for flying off the handle at the distro like that ... but it really made me feel all gates-ified inside ... *yuck* ... everybody enjoy your chunky bytes of linux, favourite flavour - whatever it may be :)

BTW : Happy Birthday to Linus Torvalds who turned 37 yesterday! :)

---

