---
title: "HOWTO: Tremulous on AMD64/x64"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by th3t1nm4n on 2006-08-10
[COLOR="Red"]This Guide is for 64-bit Ubuntu users, 32-bit users only need to do steps 1-3
Make sure that you have the latest video drivers installed.[/COLOR]

I've been working on getting all of my 32-bit linux games working on 64-bit linux and decided that since Tremulous on x64 didn't have much documentation on getting it working that I'd make a howto out of what I did and read.

1. Download the latest tremulous standalone client: [http://tremulous.net/index.php?section=files]("http://tremulous.net/index.php?section=files")

2. open a terminal and change directory to your desktop```
cd ~/Desktop/
```

3. run installer```
sudo sh tremulous-1.1.0-installer.x86.run
``` if the version you have is newer, then make sure to correct that to be the name of the file, you can do ```
ls ~/Desktop
``` to see the name of it.

4. follow through the install, the default options are fine, but still read through it in case for if you do want to install the source code or a dedicated server.
Now if you were to execute tremulous you'd get something like "tremulous.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory", that's because it needs 32-bit SDL libraries, you can get them from the repositories.

5. Install 32-bit SDL libraries from the repositories: ```
sudo apt-get install ia32-libs-sdl

``` (if for some reason you can't apt-get install them, you can find the .deb [here]("http://packages.ubuntu.com/dapper/libs/ia32-libs-sdl").)

6. Tremulous should work now, you can run it from a terminal using ```
tremulous
```, if it doesn't work you can try this: ```
cd /usr/local/games/tremulous/
sudo ln -s /usr/lib32/libSDL-1.2.so.0 libSDL-1.2.so.0

```

7. Be sure to at least skim through the manual before playing: [http://tremulous.net/manual/]("http://tremulous.net/manual/")

8. Play!

About:

Some people have successfully compiled a 64-bit version from source, but report that it runs very slow, mostly around areas of dense enteties, which is why I chose to get the 32-bit version running.

I have this running on 64-bit Dapper with the linux-amd64-k8-smp kernel on my AMD Athlon(tm) 64 X2 4200+.

Good Luck and Happy Dretching/Fragging!!!

---

### Post by Yagisan on 2006-08-11
You might find it interesting that there are dapper backports of edgys Tremulous packages for amd64 and i386 in the doomsday repo here. It's rather slow, but they are there. Just change breezy to dapper in the sources list.
[http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu)

---

### Post by th3t1nm4n on 2006-08-11
I've actually used those repositories before for jDoom, I never noticed that Tremulous was in it too. 
Thanks for this alternative. :D

---

