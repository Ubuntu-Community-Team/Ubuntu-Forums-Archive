---
title: "HOWTO: Play Windows Media Files(WMV v8 and 9) on Ubuntu Linux"
date: 2005-06-14
forum: Desktop Environments
---

### Post by paulbaranowski on 2005-06-14
I figured out how to play WMV files on Ubuntu, and I thought I would share it with others.  Please send me feedback if you know better ways to do these things.

Thanks to:
[http://blogs.eclab.byu.edu/daley/archives/2005/05/playing_windows.html](http://blogs.eclab.byu.edu/daley/archives/2005/05/playing_windows.html)
[http://gnomesupport.org/forums/viewtopic.php?t=6993](http://gnomesupport.org/forums/viewtopic.php?t=6993)


1) Download mplayer and mplayer-codecs from:
[http://luna.cs.ccsu.edu/dominik/mplayer/downloads.html](http://luna.cs.ccsu.edu/dominik/mplayer/downloads.html)
[http://luna.cs.ccsu.edu/dominik/mplayer/downloads-optional.html](http://luna.cs.ccsu.edu/dominik/mplayer/downloads-optional.html)

You probably only need the codecs, but this are the steps I took to get it working.

You will have two files:
mplayer-1.0pre7-1.i386.rpm
mplayer-codecs-20050412-1.i386.rpm

2) Convert them to debian packages:
alien mplayer-1.0pre7-1.i386.rpm
alien mplayer-codecs-20050412-1.i386.rpm

This will create the files:
mplayer-1.0pre7-2_i386.deb
mplayer-codecs-20050412-2_i386.deb

3) Install them:
sudo dpkg -i mplayer-1.0pre7-2_i386.deb
sudo dpkg -i mplayer-codecs-20050412-2_i386.deb

4) (I only got it working with Xine, so here are the steps for that app.)
Open ~/.xine/config and add the line:
decoder.external.win32_codecs_path:/usr/lib/codecs

5) (see note at the bottom for why you do this step)  
Edit mime file /usr/share/mime/packages/freedesktop.org.xml and find 

 <mime-type type="video/x-ms-asf">
    <comment>Microsoft ASF video</comment>
    ...[snip]...
    <glob pattern="*.asf"/>
    <glob pattern="*.asx"/>
    <magic priority="50">
      <match value="0x3026b275" type="big32" offset="0"/>
    </magic>
  </mime-type>

and remove the <magic>...</magic> section, save the changes.

6) Run:

sudo update-mime-database /usr/share/mime 

so the system knows about the changes you made in freedesktop.org.xml.

7) Restart Nautilus if you have it open.

8) Set Xine to be your default player for WMV files:
See "How to change default file type "Open with" program?" ([http://ubuntuguide.org/#changedefaultfiletypeprogram](http://ubuntuguide.org/#changedefaultfiletypeprogram)) and change the default player.

Done!

End Note: Why am I messing with mime types?
If you dont make this change you will get an error when you click on WMV files that are ASF:
-------------------------------------------------------------------------------
Cannot open anything.wmv
The filename "anything.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.
-------------------------------------------------------------------------------

This happens whenever Nautilus detects that the mime-type of the file doesn't correspond to the filename extension.

---

### Post by jhk on 2005-06-14
That's useful for x86 boxes.  But it's sad that you still can't play WMV files in PPC linux.  The reason given is that all the codecs are x86, but Microsoft provides Windows Media Player for Mac os X, so the codecs must exist somewhere.

And now I feel real stupid because of Apple's architecture change.  Maybe you could use x86 codecs on a Mac then?

---

### Post by DarkSilver on 2005-06-14
I don't understand !!?!
 ```
sudo apt-get install w32codecs
```and that's it ... totem can read WMV...
If you install xine, it will work too...

if you want mplayer :```
apt-get install mplayer-586
```(Add the marillat repository for the last version of codec : 1:20050412-0.0 instead of 1:20050216-0.0 of hoary extras)

---

### Post by afonic on 2005-06-14
[QUOTE=DarkSilver]I don't understand !!?!
 ```
sudo apt-get install w32codecs
```and that's it ... totem can read WMV...
If you install xine, it will work too...

if you want mplayer :```
apt-get install mplayer-586
```(Add the marillat repository for the last version of codec : 1:20050412-0.0 instead of 1:20050216-0.0 of hoary extras)[/QUOTE]
 Exactly.

Sorry to say because its a nice guide, but in ubuntu you get WMV, RealMedia and other just with 1 apt-get command (or by Synaptic). Remember you need to enable universal packages.

---

### Post by bored2k on 2005-06-14
It is actually not a nice (sorry), at least not a good Ubuntu guide. There is no reason why someone should use RedHat Packages for MPlayer when we have them native. Installing packages from another distributions is something that will never 100% as good/secure as a native.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by TeeJay on 2005-06-14
[QUOTE=bored2k]It is actually not a nice (sorry), at least not a good Ubuntu guide. There is no reason why someone should use RedHat Packages for MPlayer when we have them native. Installing packages from another distributions is something that will never 100% as good/secure as a native.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)[/QUOTE]

Hey "paulbaranowski"  I will give you props for at least trying, it is a nice guide &  would have cost you considerable time to write, so keep up the good work, you just need to research a bit more in the future.
 
There are a million ways to get the job done, if it works for you then who cares how you did it?????/

---

### Post by bored2k on 2005-06-14
[QUOTE=TeeJay]Hey "paulbaranowski"  I will give you props for at least trying, it is a nice guide &  would have cost you considerable time to write, so keep up the good work, you just need to research a bit more in the future.
 
There are a million ways to get the job done, if it works for you then who cares how you did it?????/[/QUOTE]
 I have no problem with the guide actually. But this being an official forum, the Ubuntu dev team does not like when HOWTOs with weird method are taught to people. Since I respect teh variety of decisions, as long as it works, I respect the method, but I just wanted to add it is not the ubuntu way to do it. I hope no ones feels offended.

---

### Post by paulbaranowski on 2005-06-15
Ok, feel free to delete this post then!  Sorry about that, I'm just a noob.  Thats what I get for asking google instead of the forum.

---

### Post by bored2k on 2005-06-15
[QUOTE=paulbaranowski]Ok, feel free to delete this post then!  Sorry about that, I'm just a noob.  Thats what I get for asking google instead of the forum.[/QUOTE]
 No no. The thread will stay. The beauty of Linux is one word: **choice** ! But just one tip, next google search, end it with teh word Ubuntu ;). [http://www.google.com/linux](http://www.google.com/linux)

---

### Post by nocturn on 2005-06-15
[QUOTE=paulbaranowski]Ok, feel free to delete this post then!  Sorry about that, I'm just a noob.  Thats what I get for asking google instead of the forum.[/QUOTE]

For a new user, it is really cool taht you wrote a guide for something you learned immediately.  It means you get the spirit of Free Software.

Kudos to you.

---

### Post by XDevHald on 2005-06-20
[QUOTE=nocturn]For a new user, it is really cool taht you wrote a guide for something you learned immediately.  It means you get the spirit of Free Software.

Kudos to you.[/QUOTE]
 Agreed and much respect to you on that post of guided howto. Not many or any newbies join up and pull their guts out to show others what they got even though they're new to the grounds.

Well done :)

---

