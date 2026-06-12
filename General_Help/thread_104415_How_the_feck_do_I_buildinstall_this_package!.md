---
title: "How the feck do I build/install this package?!"
date: 2005-12-16
forum: General Help
---

### Post by Mosey on 2005-12-16
So I downloaded the 'advancemame-0.99.0.tar.gz' file so I could try out this as an alternative to the buggy (and beta) GXMame.

Can someone please give me a brief walkthru on how to turn this into a package and then install it?

---

### Post by DaMasta on 2005-12-16
tar -zxvf advancemame-0.99.0.tar.gz
cd advancemame-0.99.0
./configure
make
make install

---

### Post by Arktis on 2005-12-16
A link to the file would be helpful next time... 'kay, I found it. Except there is a more up to date version availible here: [http://sourceforge.net/project/showfiles.php?group_id=33717](http://sourceforge.net/project/showfiles.php?group_id=33717)

You should get that instead. It's "advancemame-0.102.0.tar.gz".

First, you should have build-essentials installed:
```
sudo apt-get install build-essential
```

Okay, this is a pretty standard source tarball.  You need to compile it.  So, extract it by right clicking on the file and selecting "Extract Here".  Then open a terminal and cd to wherever you extracted it.  For example, if you extracted it onto your desktop, then you would do:
```
cd Desktop/advancemame-0.102.0
```
Then you need to run it's configure script so it can check out your system and set up it's make files accordingly.
```
./configure
```
then if you get no errors, run make
```
make
```
Let it do it's thing, and if it doesn't mess up and abort, then you can install it.
```
sudo make install
```

---

### Post by Lifesteeler on 2005-12-16
[QUOTE=DaMasta]tar -zxvf advancemame-0.99.0.tar.gz
cd advancemame-0.99.0
./configure
make
make install[/QUOTE]

That should do it yes, and if you're missing anything(compiler, libs.. etc.), it should say...

---

### Post by Mosey on 2005-12-16
How do I run it? I need to create a starter for it...I don't know it's run command.

---

### Post by Mosey on 2005-12-16
Is there some kind of way to tell what the run command is for a program? Shouldn't this have appeared in my applications bar after a killall gnome-panel?

---

### Post by DaMasta on 2005-12-16
No, it won't automatically appear in your panel. From the directory type ./ and the tab. You'll get a list of excutable files in there. Changes are the name of the file is advancemame, so it'd be ./advancemame. You'll have to manually add it to your panel.

---

### Post by Mosey on 2005-12-16
From the directory? I'm sorry. I don't understand?

Thank you all very much for your help and the help you'll give me.

---

### Post by DaMasta on 2005-12-16
Yeah, from the unpack directory. You've already ran ./configure, make and make install right?

---

### Post by Mosey on 2005-12-17
Wait...does this even have a GUI...like GXMame?

*Frustrated to tears*

---

### Post by Mosey on 2005-12-17
I don't know what the 'unpack directory' is...or where to find it...or even if I found it what to do with it.

I've run ./configre, make and make install...all without incident.

Don't know where to go from here.

---

### Post by crmanski on 2006-03-05
Mosey,
In the same terminal that you ran make, make install etc in you shoul simply type...

cd /usr/local/bin
advmame --default
advmenu --default

then again...
advmenu

I have not actually been sucessfully at running the program yet. I am in the process of recompiling like mentioned here...
[http://ubuntuforums.org/showthread.php?t=106817&highlight=AdvanceMAME](http://ubuntuforums.org/showthread.php?t=106817&highlight=AdvanceMAME)

---

