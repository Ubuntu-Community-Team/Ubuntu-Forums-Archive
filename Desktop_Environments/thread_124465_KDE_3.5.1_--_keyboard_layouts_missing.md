---
title: "KDE 3.5.1 -- keyboard layouts missing"
date: 2006-02-01
forum: Desktop Environments
---

### Post by hogweed on 2006-02-01
Yikes! I just upgraded to KDE 3.5.1 using the Kubuntu repos, and suddenly have lost my keyboard layouts. These were working fine in 3.5.0, but suddenly seem to have vanished. I am hoping to regain the US keyboard with the deadkeys.

Where, oh where have these gone? I have a tough time writing and getting work done without these...

Any ideas?

-- hogweed

---

### Post by Gerardo Santo on 2006-02-01
Damn - with me happened the same... :-k

---

### Post by z-vet on 2006-02-01
Same here.

---

### Post by 0xBulbizarre on 2006-02-02
As a **temporary** fix, and **if** your keyboard is correctly configured in xorg, you can delete ~/.kde/share/config/kxkbrc
then restart kde.

Arnaud

---

### Post by igorchik on 2006-02-02
I have the same problem. :confused:

---

### Post by ashrack on 2006-02-02
4M it's looking like this. 
[ATTACH]5791[/ATTACH]
is it the same 4 U all?

---

### Post by igorchik on 2006-02-02
yes, I have this problem. Do you know solution? :rolleyes:

---

### Post by hogweed on 2006-02-02
[QUOTE=0xBulbizarre]As a **temporary** fix, and **if** your keyboard is correctly configured in xorg, you can delete ~/.kde/share/config/kxkbrc
then restart kde.

Arnaud[/QUOTE]

This didn't work for me. I am really surprised that something this basic has gone awry. Thankfully I have another computer that I did not upgrade yet, so I can work using that one until I have time to downgrade my primary machine back to KDE 3.5.0. This is really not a good situation. Hopefully the Kubuntu folk will come out with an update that fixes this very, very soon...

-- hogweed

---

### Post by hogweed on 2006-02-03
Ok, so it looks like the kcontrol module controlling keyboard layouts is completely broken. I attempted to activate keyboard layouts and then manually paste the proper code into the "command" section in order to get the us(intl) keyboard layout. (this is the command: setxkbmap -model  -layout us -variant intl)

But even after enabling keyboard layouts (which simply gives the blank non-entries that you can see in ashrack' post, the "command" entry simply is dead. No possibility of pasting, typing, anything in there.

So, I will downgrade until this gets fixed...

-- hogweed

---

### Post by hogweed on 2006-02-03
Oh, and here is one of the bugreports that has been filed:

[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/30295](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/30295)

-- hogweed

---

### Post by ashrack on 2006-02-04
Silly question, does this only happen on UBUNTU distros or is it distro spread?
If so the BUG REPORT on LAUNCHPAD won't do any good since it's only KDE related, IMHO

---

### Post by z-vet on 2006-02-04
It looks like it's Ubuntu-specific: no new bugs were open on KDE's Bugzilla (i do believe that if it was distro-spread there were a bug reports already).

---

### Post by JvdS45 on 2006-02-04
still missing 2 days ago

it get worse now :| so developers where are u now :|

---

### Post by treris on 2006-02-04
no keyboard layouts here either, and I've tried a bunch of the fixes offered here and in other threads, but sofar nothing seems to work

kinda weird that something this basic, which has been working perfect since, I don't know, at least warthy, is now broken
it's like the database with all the keyboard layouts in it has been completely emptied or something, 

maybe a wrong symlink somewhere?? I'm not a programmer or anything, but hey just a thought

---

### Post by hogweed on 2006-02-04
Well, I have gone ahead and downgraded. I had hoped that an update to this would have happened by now.

In the meantime, I have been using the Gnome desktop in Ubuntu -- this is very, very nice, and I really see why some people prefer it. Perhaps once Dapper rolls around I will give it a shot, since by then I will actually have some time on my hands to explore a bit more and get things working the way that I want. But, till then, it is back to KDE 3.5.0.

-- hogweed

---

### Post by treris on 2006-02-04
what would be the quickest way of downgrading?? will just removing the kde 3.5.1 repo's and then reloading all in synaptic do the trick or what?
not having keyboard layouts available is just to much of a hassle and kde 3.5 worked just fine for me

---

### Post by limit223 on 2006-02-04
There is actually a bug report filled up in KDE bug list:
[http://bugs.kde.org/show_bug.cgi?id=121249](http://bugs.kde.org/show_bug.cgi?id=121249)

stay tuned for the news!

---

### Post by treris on 2006-02-05
I've found a fix for this problem in kubuntuforums
there is indeed a need for a symlink

this is what I found and it has worked for me perfectly

[http://kubuntuforums.net/forums/index.php?topic=3102.msg12587#msg12587](http://kubuntuforums.net/forums/index.php?topic=3102.msg12587#msg12587)

hope this works for everybody

---

### Post by Alpha_toxic on 2006-02-05
Great!! This actually worked!!!  :D

---

### Post by KuA on 2006-02-05
Yes indeed! A symlink was missing! So with

# cd /usr/share/X11/
# sudo ln -s /etc/X11/xkb/ xkb

the problem gets solved. Just fire

# kcmshell keyboard_layout

and the layouts are back again. :)

---

### Post by igorchik on 2006-02-05
Thank You all!
It work for me :)

---

### Post by ashrack on 2006-02-05
will there be an official fix for this, via SYNAPTIC?

---

### Post by sunny_nwho on 2006-02-11
fabulous u folks are gr8...it worked

---

### Post by hogweed on 2006-02-11
Great! Thanks all -- I knew it was something dumb like this...

-- hogweed

---

### Post by zi99y on 2006-02-20
Blimey! Seek and you shall find indeed.

My volume keys are working again :mrgreen:

---

### Post by ispmarin on 2006-02-21
Same problem... and good solution. Makes me very happy!
Did anybody, maybe the guy who filled the bug report, posted there the correction?

Cheers

Ivan

---

### Post by Proleter on 2006-02-22
Finaly did it! 
I couldn't understand the ln command, so I have been trying from diferent folder.
Thanks for the help.

---

