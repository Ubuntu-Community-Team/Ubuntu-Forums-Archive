---
title: "Help with upgrading to kde3.5 on Kubuntu Breezy"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Princey on 2005-12-14
Hey guys, sorry if that's covered in some post but after an hour of searching I can't seem to lay hands on the right post. I've been out of state for a month now and came back a few days ago. I logged in to the forum after reading in Tux Magazine that KDE 3.5 was out. Did some searching around on the kde.org website and here in the forum and the common solution was the basically the same:

"KDE 3.5 has been released. You can download the KDE packages from any of these sources (add to /etc/apt/sources.list):
These packages have been digitally signed using Jonathan Riddell's key. A copy of they key is also kept on people.ubuntu.com for verification. To add this key do:
 wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

Kubuntu 5.10 (Breezy)
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main"

Well, I fired up konsole and typed in "sudo kwrite etc/apt/sources.list" to edit my etc/apt/sources.list so I can update but I keep getting this message at the prompt:

"Error: "/tmp/kde-princey" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"

Am I doing something wrong or what? I'm still learning Linux, so I rather ask for help than tinker my box unusable. Anyhelp is appreciated as to what should I do and what next. Thanks

---

### Post by MartinG on 2005-12-14
[QUOTE=Princey]Well, I fired up konsole and typed in "sudo kwrite etc/apt/sources.list" to edit my etc/apt/sources.list so I can update but I keep getting this message at the prompt:

"Error: "/tmp/kde-princey" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"

Am I doing something wrong or what? I'm still learning Linux, so I rather ask for help than tinker my box unusable. Anyhelp is appreciated as to what should I do and what next. Thanks[/QUOTE]

You'll get this complaint because you're using sudo, but it *should* still start kwrite -- are you saying it doesn't?  Also, the url bit needs a leading /, to give /etc/apt/sources.list

---

### Post by Princey on 2005-12-14
[QUOTE=MartinG]You'll get this complaint because you're using sudo, but it *should* still start kwrite -- are you saying it doesn't?  Also, the url bit needs a leading /, to give /etc/apt/sources.list[/QUOTE]

It does start kwrite but with a blank kwrite window, nothing in there.

---

### Post by MartinG on 2005-12-14
[QUOTE=Princey]It does start kwrite but with a blank kwrite window, nothing in there.[/QUOTE]

My guess is that's because you got the filename incorrect, as in my last post. It MUST begin as /etc/... not etc/..., otherwise it's trying to edit a non-existent file

---

### Post by Princey on 2005-12-14
[QUOTE=MartinG]My guess is that's because you got the filename incorrect, as in my last post. It MUST begin as /etc/... not etc/..., otherwise it's trying to edit a non-existent file[/QUOTE]

Thanks, I'll give it a go as soon as I get home. I'll post back with the results.

---

### Post by Princey on 2005-12-14
Thanks a lot, it worked like a charm. I'm up and running now using kde 3.5. I never realised in your first answer that I was leaving out the leading /

---

### Post by MartinG on 2005-12-14
That's great.  Enjoy!

---

### Post by leech on 2005-12-14
I installed this on my desktop, but unfortunately it was very crash prone.  So I figured what the heck and updated to the full Dapper release of KDE 3.5  And it's a HUGE difference.  Now I have shadows and fade in stuff all over the place... well a little too much of it really, and with KDE's billion dialogs, it isn't really easy to find exactly where it is to change the speed (it needs to fade in and out a bit faster) any help would be welcomed here....

Leech

---

### Post by MartinG on 2005-12-15
Interesting ... I'm about to do a test install of Dapper Flight 2, though for me KDE3.5 is good on Breezy. I suspect I'll leave a "working" Dapper till the betas start arriving.

---

