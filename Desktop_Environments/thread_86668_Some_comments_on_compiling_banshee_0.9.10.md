---
title: "Some comments on compiling banshee 0.9.10"
date: 2005-11-06
forum: Desktop Environments
---

### Post by pizzach on 2005-11-06
It's a pain in the butt compiling 0.9.10!  The version needs even more bleeding edge stuff than that is in breezy at the moment.  So I compiled mono even though I realized late that I actually didn't need to (using ./configure --with-internal-mcs) and a bunch of other stuffs usually with the naming scheme of something-sharp.  With the mono linker/compiler/whatever being included I probably could have gotten away with sudo apt-get build-dep banshee in hindsight. :mad: 

You get a very strong impression of a windows program with how it makes it's executable as banshee.exe.  Reminds me how the program creates a "My Music" folder a la windows when you're running it.  It also installs it in a weird directory by default (/usr/local/lib/banshee/).  I don't see any other executables in the lib directory so it's probably not the right place for it.  The Banshee from Ubuntu's servers does seem to install in the right directory.  Or at least a different one. :)

After compiling and installing 0.9.10 I had to go to synaptic and reinstall all of my gstreamer stuffs because banshee borks them good.  You can't run anything that uses gstreamer anymore otherwise including rhythmbox.  Last, in order to make banshee run, I had to make a shellscript in /usr/bin pointing to /usr/local/lib/banshee/banshee.exe and delete the link they made which I believe was is /usr/local/bin/.  I don't remember why, but typing "banshee" just gave errors in the terminal otherwise.

So this is just a warning to all of you that might be thinking of compiling it.  ;) They might have fixed the stuff in cvs already but I haven't checked personally.  Anyone else fight as much as me with compiling it?  It's been talked about to death, but I find myself stuck in between rhythmbox and banshee.  The each have the features that the other is missing.  :rolleyes:

---

### Post by Manny C on 2005-11-06
I'm sure Banshee hackers (yes...you know who you are ;) ), will be able to help this poor soul see that Bleeding Edge banshee is not for the faint hearted! ;)

Seriously though pizzach, an ubuntu user/banshee hacker friend of mine, found it an enormous pain in the royal side to install the latest banshee. He found that some files he had that were scanned by Banshee were written down to 0 bit files..that is bad news.

I understand .9.10 is a major feature kick, but you are gonna have to hold out. Either that, or you are going to have to put up with brokeness ;). Ah the beauty of bleeding edge.

---

### Post by pizzach on 2005-11-06
Yeah, that is why I at least stayed away from the cvs.  I figured it would be more dangerous than the releases which are semi-dangerous.  I am proud to have gotten it working though.  It's all about the challenge.  (I also just managed to compile vlc too. AGH.)  0 bytes eh?  Talk about lossy compression...

The program actually looks nicer now over 0.9.8.  Now that I'm done looking at it, I'm still back to using rhythmbox. :)  I find rhythmboxes category listings infinitely useful.

In any case, I'm asking myself if I should attempt a howto on compiling it for Ubuntu. hm...

---

### Post by Manny C on 2005-11-06
You will have help shortly...

---

### Post by RAOF on 2005-11-06
The two most important steps to building banshee (0.9.9+ or CVS) are
--with-internal-mcs and --prefix=/usr.  Adding both of these options to ./configure (or, for CVS, ./autogen.sh) allowed me to build banshee.  (After a long, arduous, and sadly pointless round of mono fiddling).

The first option is obvious - use the supplied mcs which does not have the bug which makes the Breezy (1.1.8.2) mcs fail to compile banshee.  

The second option, --prefix=/usr, will install everything under the /usr directory.  This is where Ubuntu stuff is put by default, including the **mono Global Assemblies Cache**.  I believe this is why my banshee build, at least, would fail to run with "assembly not in cache".  Many other distros put stuff under /usr/local (for locally installed stuff, like this), and it's the default install point for banshee.

If you build banshee (and all of it's support libs, libipoddevice & ipod-sharp) with --prefix=/usr, it should work.

---

### Post by pizzach on 2005-11-07
Meh.  The new banshee webpage appears to be a lot more thorough.  Think it basically comes down to this:

sudo apt-get build-dep banshee
cd banshee*
./configure --prefix=/usr --with-internal-mcs
make
sudo make install

and you're good.  Maybe.  Of course I compiled the pod plugins and mono and don't remember what I did with their prefixes.  I only started using it halfway though when I finally figured out what they were.  That is probably why my installation wasn't as simple as it should have been.  Meh.  Live and learn.  It doesn't look to hard to compile when it's all spelled out and you figure out you can avoid a lot of the steps.

---

### Post by XQC on 2005-11-07
Ok, now I got, that it is a bit of a hassle to compile Banshee...

But it is actually worth it?
Screenshot anyone?

---

### Post by vassie on 2005-11-08
I installed 0.9.10 last night

[Here]("http://www.flickr.com/photos/benvassie/") is some screenshots

I am going to write a procedure on how I installed it, as it wasn't easy!

Ben

---

### Post by vassie on 2005-11-08
Hope this helps

[http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/](http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/)

Ben

---

### Post by XQC on 2005-11-08
Great work! :)
Works fine for me.

Though I would prefer "sudo checkinstall" rather than "sudo make install" because with checkinstall you can remove the packages easily with Synaptic when anything doesn't work.

---

### Post by pizzach on 2005-11-09
[QUOTE=vassie]Hope this helps

[http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/](http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/)

Ben[/QUOTE]


Impressively nice.  Thanks for saving me the work Ben.  :)

---

### Post by vassie on 2005-11-09
Hello,
I'm glad people are finding it useful :)
BTW, I have just created deb's of of libipoddevice, ipod-sharp & banshee 0.9.10 using checkinstall.
You can find them here [http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/]("http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/")
Ben

---

