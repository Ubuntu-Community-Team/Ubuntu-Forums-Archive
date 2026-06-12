---
title: "Question about Superkaramba"
date: 2005-07-23
forum: Desktop Environments
---

### Post by arunsub on 2005-07-23
I'm using Superkaramaba in Kubuntu. I have installed Liquid weather theme through Superkaramba. It's not showing up in the desktop. How to make it show in the desktop? I'm using a different KDE desktop theme than the default one. Is that a problem?

---

### Post by Xian on 2005-07-23
Do you have any type of transparencies enabled?
That can sometimes cause issues.

Switch to the default theme. Does it work then?

---

### Post by Freddy on 2005-07-23
The new version of Liquid Wheater needs to be run on Superkaramba 0.37, the one you can find precompiled for Kubuntu is 0.36.

You can find a 0.37RC1 for Debian but that one is compiled with debian named dependencies, I tried to install it and the deb version works but it shows up as broken package in Synaptic, the other choice you have is to compile it yourself, witch I did.

Superkaramba 0.37 is awsome and I recommend all those who use Superkaramba to use it. = )

/Freddan

---

### Post by geearf on 2005-07-23
Hello i am using the 0.36 + old liquid weather, are the new ones really interresting ?

---

### Post by elsewhere on 2005-07-23
0.37 seems a lot more user-friendly, you can check out a couple of screencaps [here](http://www.kde-look.org/content/show.php?content=23258) on kde-look.org.  Right off the bat, the biggest improvement for me is that it "remembers" themes you've run before and can launch them.  I had a bad habit with previous versions of superkarmba of accidentally shutting it down, and then having to reload each theme individually.  Also, and they've finally gotten rid of the "bomb" icon in the taskbar and replaced it with something a little less abrasive.  You even have an option to hide it.

Even though it's RC1, I haven't had a stability issue yet.  As Freddy pointed out, it needs to be compiled for kubuntu but it's a straight-forward compile as long as you have the proper kde dev packages installed.  I didn't have any errors or problems compiling myself.

Cheers,
KV

---

### Post by f1dave on 2005-07-24
hmm. maybe i should look at 0.37.

Does kde session manager recognise it yet?

---

### Post by geearf on 2005-07-24
it looks nice yes, i may use it later.

---

### Post by elsewhere on 2005-07-24
[QUOTE=f1dave]hmm. maybe i should look at 0.37.

Does kde session manager recognise it yet?[/QUOTE]

Yes, any themes you have running when shutting down will autoload next time you log in, if that's what you mean...

Cheers,
KV

---

### Post by Freddy on 2005-07-24
I did have some problem compiling it though, not that hard to solve but was missing som importent dependencies like python dev, kde headers and such, I had a pretty clean install of Kubuntu. Just install those dependencies that the configure script is asking for, you can find all in your repos, so just fire up Synaptic or Kynaptic (or use big Bash :)) when installing

I've been using it for a few days now and haven't noticed any bug at all (at least not yet ;))

Superkaramba 0.37 is a big step forward from 0.36 and I'm quite happy with it.

/Freddan

---

### Post by raggamuffin on 2005-08-07
Hi, another liquid weather question...

I installed the newest SuperKaramba version, and downloaded the Liquid Weather theme, but when I load the LW theme, all I get is a blank black window for it?...(see screenshot at [http://img7.imageshack.us/img7/4083/screen27fw.jpg](http://img7.imageshack.us/img7/4083/screen27fw.jpg) )...

when I try right-clicking and going to "Configure theme", the "Configure theme" is greyed out so I can't click on it...and I don't know how to fix this...

Does anybody have any suggestions?...Thanks in advance...

---

### Post by f1dave on 2005-08-08
The newest for both as i type this is 8.2 for liquid weather and 0.37 RC2 for superkaramba. Are these the ones installed on your system?

---

### Post by raggamuffin on 2005-08-08
[QUOTE=f1dave]The newest for both as i type this is 8.2 for liquid weather and 0.37 RC2 for superkaramba. Are these the ones installed on your system?[/QUOTE]

yes...

---

### Post by muzza on 2005-08-16
[QUOTE=Freddy]......You can find a 0.37RC1 for Debian but that one is compiled with debian named dependencies, I tried to install it and the deb version works but it shows up as broken package in Synaptic, the other choice you have is to compile it yourself, witch I did......
/Freddan[/QUOTE]

I've just installed Superkaramba 3.6 using Synaptic, but liquid weather doesn't work and I don't know how to 'compile'.

Could someone write a simple 'howto' for me, or is it a complicated exercise?

---

### Post by f1dave on 2005-08-16
Easy enough to do muzza.

1. Grab the tar file provided, ie the source
2. Extract to a directory of your choice using ark or alternatively with the console
3. in console run:
     ./configure (this will tell you if you have all the required libraries)
     make (this will build the program)
     sudo make install (this will install the program)
4. Use the wonder of widgets to your hearts kontent!

Hope that helps.

---

### Post by f1dave on 2005-08-16
[QUOTE=raggamuffin]Hi, another liquid weather question...

I installed the newest SuperKaramba version, and downloaded the Liquid Weather theme, but when I load the LW theme, all I get is a blank black window for it?...(see screenshot at [http://img7.imageshack.us/img7/4083/screen27fw.jpg](http://img7.imageshack.us/img7/4083/screen27fw.jpg) )...

when I try right-clicking and going to "Configure theme", the "Configure theme" is greyed out so I can't click on it...and I don't know how to fix this...

Does anybody have any suggestions?...Thanks in advance...[/QUOTE]

Sorry, missed your post there.

Ok... first and foremost, have you tried both updating and reloading the theme with the right click?
If so, try loading up liquid weather, then restarting your x server. Sometimes I get a weird bug happening similar to what you describe, and that's how I fix it. When your x server restarts, your superkaramba should automatically load LW.

---

### Post by muzza on 2005-08-16
[QUOTE=f1dave]Easy enough to do muzza.

1. Grab the tar file provided, ie the source
2. Extract to a directory of your choice using ark or alternatively with the console
3. in console run:
     ./configure (this will tell you if you have all the required libraries)
     make (this will build the program)
     sudo make install (this will install the program)
4. Use the wonder of widgets to your hearts kontent!

Hope that helps.[/QUOTE]

Thanks for that f1dave, but I have uno problemo.
1. OK, easy enough
2. OK, I extracted the tar file (I think) I made a directory and called it Superkaramba, that's where I extracted it to.
3. I failed at this step.  I typed ./configure in console and got this;

[COLOR=Blue]muzza@kubuntu:~ $ ./configure
bash: ./configure: No such file or directory[/COLOR]

I didn't think it would be that easy, What did I miss?

**_[COLOR=Red]EDIT[/COLOR]_**
I've tried to 'cd' to the directory where I extracted to before typing ./configure.  This finally got it to 'configure' but I had errors?? I don't understand what to do next.

Here's what the console reported;

[COLOR=Blue]muzza@kubuntu:~ $ cd /home/muzza/superkaramba/superkaramba-0.37-RC1
muzza@kubuntu:~/superkaramba/superkaramba-0.37-RC1 $ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
muzza@kubuntu:~/superkaramba/superkaramba-0.37-RC1 $[/COLOR]

What do I do next??

**_[COLOR=Red]ANOTHER EDIT[/COLOR]_**

I studied the above and decided to synaptic for 'gawk' and 'gcc'.  They weren't installed, so I installed them and then 'configure' failed because something else was missing.  So I installed 'g++', then 'g77' and so on, and so on.....

[COLOR=Blue]muzza@kubuntu:~/superkaramba/superkaramba-0.37-RC1 $ ./configure

(I've cut a chunk out to save space) 

checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
muzza@kubuntu:~/superkaramba/superkaramba-0.37-RC1 $[/COLOR]

Do I have to synaptic/install ALL of the things that say '...no' ??
I think that I also failed the 'sanity check'!

I have searched everywhere, and all the instructions that I have found just tell me to type;
./configure
make
sudo make install

Sounds easy enough.  Why am I making it so difficult?

I've kept installing the missing bits, and it still won't let me play. 

Now the last few lines say this;
[COLOR=Blue]checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths![/COLOR]

That's it.  That's as far as I can take it without expert tuition.  I hope I haven't bloated my installation with unneccessary junk.

Sorry if I'm being stupid, but have I missed something ridiculously simple???????

**[COLOR=Red]YET ANOTHER EDIT[/COLOR]** 

I've just kept plugging away at this.  I seem to get further each time, but something else stops the process.

Now, console tells me this;

[COLOR=Blue]checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for IceConnectionNumber in -lICE... no
checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.
[/COLOR]

Back to Synaptic - I searched for libxext - found 'libxext6' + 'libext6-dbg' + libext-dev' - installed all of them, and 'configure' reports the same fault.

I've installed libxext, why won't it let me play?

---

