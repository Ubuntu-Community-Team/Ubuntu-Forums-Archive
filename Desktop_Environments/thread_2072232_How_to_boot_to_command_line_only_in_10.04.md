---
title: "How to boot to command line only in 10.04"
date: 2012-10-17
forum: Desktop Environments
---

### Post by houseworkshy on 2012-10-17
I know this question has been posted before, I've searched, however this may be a sepecial case which is why I'm posting seperately.  I duel boot Mepris and Ubuntu 10.04, they have a drive each and the loader is on the Mepris drive.  I also have 1.8 gig RAM of which Gnome 2 uses nearly a whole gig.  I'd like to be able to boot to the command line to free up some RAM.
In early versions of Ubuntu one could choose to boot to command line only on boot.  Later one had to hold down or press the shift key to get to the boot options.  On my machine this no longer works.
So I've tried going via a virtual terminal, +Control +Alt +Funtion Key, which does work but "free" shows that I'm still using just as much RAM actually slightly more which isn't useful.  Booting to Xterm doesn't save RAM either.  I tried "sudo stop gdm" which gave what looked like a command cursor but it isn't; it can be typed from, the letters appear on the screen,  and the return key starts a new line but commands don't work, I tried several, man, ls, exit, and some others.  Then tried the same command with 'services' in it and services wasn't recognised.
Searching here I have found some solved posts which all involve editing the grub.  I don't really want to do that as I'm only wanting a quick play of something which struggles with .8 gig, 0ad.  So is there a way to get that old Ubuntu booting to the command line mode, or properly killing the GUI and going to the command line, back more easily?

---

### Post by PowerBarry43 on 2012-10-17
Hi

I've found some info [here]("http://askubuntu.com/questions/76543/how-do-i-disable-gdm-and-graphical-user-selection") on stopping GDM from starting, you could also kill x after it starts if you can find its process in ps aux, alternatively you could download and install ubuntu 10.04 server as that comes with no GUI. Unfortunately you will need to backup all your data as it will be wiped when you reinstall.

Hope this helps!

Barry

---

### Post by houseworkshy on 2012-10-17
Thanks for the extreemly fast response.  It's only a game I want to play so I don't want to change my entire operating system because of it,  though it does feel peculiar not knowing how to easily go to command line only in a linux distrubution.  Thanks for the info I'll read it now.

---

### Post by Lars Noodén on 2012-10-17
> **houseworkshy said:**
> I tried "sudo stop gdm" which gave what looked like a command cursor but it isn't; it can be typed from, the letters appear on the screen,  and the return key starts a new line but commands don't work, I tried several, man, ls, exit, and some others.  Then tried the same command with 'services' in it and services wasn't recognised.

That will give you your text-only system.  However, you first have to switch to an available console.  So after you stop gdm, press ctrl-alt-f1 and that will bring you to the first console.  You can then log in and run what you want as long as it does not need X.

---

### Post by houseworkshy on 2012-10-17
That sounds perfect, thankyou.  I shall log out and try that now.

---

### Post by SlugSlug on 2012-10-17
what game is it?

---

### Post by houseworkshy on 2012-10-17
The game is 0ad, as in zero a d, not quite finished, single player is playable though the AI for navel maps doesn't work yet,  but very nice indeed.  
Stopping gdm and then logging in to a terminal via the Fn keys worked.  Oddly a lot of ram is still being used somewhere though there is a saving, 'free' in a terminal in the gdm said 948264 was being used,  whilst 'free' in the terminal without gdm gave '789364'.  I'll top around a bit and try to work out what is using it.
I think 0ad must use X as that didn'd work outside the gdm.  
That said I'm very glad to know how to exit the GUI and go to the command line when needed and without having to edit system files.  Thanks very much for the advice.

---

