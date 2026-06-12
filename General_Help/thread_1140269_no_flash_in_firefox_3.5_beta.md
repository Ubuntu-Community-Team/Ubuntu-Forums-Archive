---
title: "no flash in firefox 3.5 beta"
date: 2009-04-27
forum: General Help
---

### Post by notatoad on 2009-04-27
does firefox 3.5 look for plugins in a different directory than firefox 3.0?  i installed the 3.5 (or is it 3.1?) beta, and it claims i don't have flash installed, but flash works fine in 3.0.x.  i am on jaunty x64 and installed flash 10 64-bit by downloading libflashplayer.so off the adobe site and copying it to ~/.mozilla/plugins.  firefox 3.5 is just running out of a directory in my home folder.

firefox 3.5 sees all the other stuff in my ~/.mozilla folder fine (extensions, profile), and i don't have any other plugins installed so i don't know if it would see them or not.

---

### Post by fooman on 2009-04-27
> **notatoad said:**
>   firefox 3.5 is just running out of a directory in my home folder.

does the firefox 3.5 directory have a folder in it called "plugins"?

if so,  try copying the libflashplayer.so file to that folder and see if it works.

if that does not do it...maybe try copying libflashplayer.so to a more system wide location like /usr/lib/mozilla/plugins

---

### Post by notatoad on 2009-04-27
> **fooman said:**
> does the firefox 3.5 directory have a folder in it called "plugins"?

if so,  try copying the libflashplayer.so file to that folder and see if it works.

if that does not do it...maybe try copying libflashplayer.so to a more system wide location like /usr/lib/mozilla/plugins

no luck with either /usr/lib/mozilla/plugins or ~/firefox/plugins :(.  any other thoughts?

---

### Post by phil888 on 2009-05-10
Are you running a 64 bit beta?

---

### Post by Yellow Pasque on 2009-05-10
> **phil888 said:**
> Are you running a 64 bit beta?
That was my first thought. Make sure the FF 3.5 beta you installed is actually 64-bit. Go to Help -> About, and make sure you don't see any 'i686' or similar. You should only see 'x86_64'

If you are running FF 3.5 64-bit, try starting it from a terminal and see if it outputs any erros.

---

### Post by bass0 on 2009-05-10
Hi, same problem here. I tried linking the plugin library to every firefox-related directory I could find:

/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins
/usr/lib/firefox/plugins
{firefox 3.5b4 directory}/plugins

No luck. The about window is kinda vague:

> Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1b4) Gecko/20090423 Firefox/3.5b4

Oh yeah, almost forgot:

> LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]

---

### Post by jeffsa12 on 2009-05-10
I'm using FF 3.5b4pre and flash is working. I added a source to the repos to load it using Synaptic. 

I'm thinking you may have 32 bit loaded based on your:

> Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1b4) Gecko/20090423 Firefox/3.5b4 

mine is:

> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1b4pre) Gecko/20090330 Ubuntu/8.10 (intrepid) Shiretoko/3.5b4pre

Also, perhaps it's that I'm running a diff version (Gecko/20090330 Ubuntu/8.10 (intrepid) Shiretoko/3.5b4pre) .

Hope this helps....

---

### Post by zika on 2009-05-10
> **bass0 said:**
> Hi, same problem here. I tried linking the plugin library to every firefox-related directory I could find:

/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins
/usr/lib/firefox/plugins
{firefox 3.5b4 directory}/plugins

I have it linked in:
/home/zika/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
and that combination proved to be necessary and sufficient ... :) both for 3.5 3nd 3.6 ...
(as far as I remember You might not have .mozilla directory so You might have to create it ...)
try that ...

---

### Post by Yellow Pasque on 2009-05-10
> **bass0 said:**
> Mozilla/5.0 (X11; U; Linux **i686** (x86_64); en-US; rv:1.9.1b4) Gecko/20090423 Firefox/3.5b4 

The i686 indicates you're using a 32-bit browser. The other message you quoted indicates that the browser recognized libflashplayer.so, but couldn't use it because it's a 64-bit shared library.

Either install a 64-bit version of FF 3.5 or put a 32-bit version of libflashplayer.so in {firefox 3.5b4 directory}/plugins

---

### Post by jeffsa12 on 2009-05-10
Never mind.............I see Temüjin beat me to it while I was reviewing my post.....



Check this out first....about "wrong ELF class". 

[http://ubuntuforums.org/showthread.php?t=435940](http://ubuntuforums.org/showthread.php?t=435940)


Below is what I did for 64 bit flash support in FF 3.0.10

1) Downloaded flashplayer from here:  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

2) Extract the archive. You will end up with a "libflashplayer.so" file.

3) Now, open Nautilus, open your Home folder, view Hidden Files.

4) Enter the .mozilla folder and create a new directory called plugins.
 
4) Put the "libflashplayer.so" file in the plugins folder.

5) Test.

Done...

For FF 3.5beta with flash support I:

1) Add repository for FF 3.5 from here:

[http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu)

2) Use Synaptic to install FF 3.5.

Flash will now work in either version of FF.....with no extra work.

Then I disabled the FF 3.5 repo.

If you:

./ configure
make
make install

to install a test versions of FF,

Not sure as I haven't tried it.

If I can help with file links, etc let me know.

---

### Post by bass0 on 2009-05-12
Thanks jeff12sa, I ran into trouble though.

I installed the "firefox-3.5" package and its dependencies in synaptic, but after running /usr/bin/firefox-3.5 I get a segmentation fault.

I'm unexperienced and confused when it comes to locating and launching apps in linux (using MacOS as my main OS), so I might've overlooked something here.

I'm not sure where to find a 64-bit version to download. Can't find it on mozilla.com. Did you compile it yourself, by any chance?

Are there other generic ways to find out if an app is 64-bit?

---

### Post by frenezulo on 2011-10-06
I believe I have this problem sort-of licked. The solution turned out to be simple on my system, which is Debian Squeeze 64-bit, with Firefox 4.

I just download the 32-bit version of the flash plugin from Adobe. I installed it in /usr/lib/mozilla/plugins and renamed it to libflashplugin-32.so

It still doesn't work for Konqueror, but now I can at least play flash in firefox

I also got rid of all the silly nspluginwrapper stuff for good measure. Can't figure out what it really does anyway.

Basically, Firefox just doesn't work with the 64-bit plugin.

---

### Post by dcstar on 2011-10-07
> **frenezulo said:**
> 
.........
Basically, Firefox just doesn't work with the 64-bit plugin.

Rubbish, I have been using the 64-bit flash plugins for years now.

---

