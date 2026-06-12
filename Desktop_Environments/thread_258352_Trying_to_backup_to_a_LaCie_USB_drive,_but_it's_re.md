---
title: "Trying to backup to a LaCie USB drive, but it's read only?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Shigglyboo on 2006-09-15
I'm real confused on this one.  I need to get some files off my computer, because I need to install windows.  Now, after using Linux, I officially hate windows with a passion, I had to pay $90 on eBay to get a copy of it (after I already bought a laptop that came with a legit copy, but no disc...)  I'd love to stay with Linux, but no support from ANY manufacturer is sorta a big drawback..... but anyway.....

I power on the drive, and it shows up, I can browse it, and I can copy files off of it.  As soon as I try to delete something, or copy something to it, "permission denied, read only".  I can't even change the properties.  I've scoured the web on this issue and the only thing I've seen is some 'at your own risk' type fix that threatens to corrupt my computer and my hard drive.

All I want to do I copy a file off my computer and onto an external hard drive....  THIS is one of the many reasons why I must regretfully go back to windows.  I really like linux, even though I've had to do insane amounts of research just to do things like play mp3's, watch videos on youtube, etc.

I think the whole "root user" thing might be the issue here.  I was under the impression that if I went into terminal, ran that little script that makes root show up, that I was logged in as the root user... I'm guessing no.    

Under System>Admin>login window>security I have the box that says "allow local system administrator login" checked.  on some faq I found, it says to do exactly that, only the text listed for the box is somewhat different.  Until now I haven't had to actually post for anything, all the answers have been out there.  And considering the nature of potential linux users, and people who are forced to go back to windows to run the necessary software, why do I have to register to post?  Now I've got another registration that I won't ever use a week from now.  I'm planning to get another drive and install linux on the external drive, but I want the version with the rotating 3D cube and all the other eye-candy, seedoo I think someone said?....  xgl, I tried it out in ubuntu, but no dice...

oh well, sorry for ranting here, I'm beyond frustrated, I use my laptop to dj live with, and I've been out of commission for a little while now, I finally get my windows disc, and I find out a simple copy/paste action is not possible without some serious jumping through hoops...........................](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

thanks if anybody can help me.

-wes

---

### Post by slimdog360 on 2006-09-15
to copy
```
sudo cp /where_files_are/ /media/LaCie_USB_drive/
```

you could also try this to give the drive more privliges
```
sudo chmod 777 -R /media/LaCie_USD_Drive
```

If you dont like how Ubuntu works you can always try another distro. One which comes to mind is mepis. Its like Ubuntu but comes with all of the propritary stuff.

---

### Post by Shigglyboo on 2006-09-15
I tried the second line and it says the directory doesn't exist.  As far as the first one, how exactly do I figure out the exact location in terms of folders?  I was mabye 7 the last time I actually navigated and knew what I was doing with a command prompt.  Is there a way to find a folder with your file browser and translate that into the directory text?

sorry I guess that's horrible of me, but I'm completely guilty of copying and pasting code with complete trust in the linux community with no idea of what the commands actually mean (well maybe some idea).  I know about, cd, cd .., and how to view the contents of my current directory.  I don't know how get to my desktop though, or anywhere where it looks familiar.  :-\"   

and nothing personal against ubuntu, but I'd say the learning curve would put off most users familiar with a "click next and everything will be ok" type mindset.  to do basic functions of a windows/mac machine you must jump through proverbial hoops, honestly it's not that hard, but compared to almost nothing, it seems like a lot.  I would really like to see Linux conquer, and I think I'll start trying out some other distros, either way I'm not giving up completely, the overall experience is a joy to work with compared to windows, from the look and feel to the stability and overall functionallity.  just gotta get that compatibility factor.

thanks for helping,

-wes

---

### Post by slimdog360 on 2006-09-16
that second line you had to change the LaCie_USB_Drive bit to say something like sda1. Though it could be called something different.

if you open up the window manager, like you do for the copy/paste stuff, you can see where you are by looking at the url bar up the top. If you are in your home folder it will say /home/Shigglyboo/, you can go back a couple of folders by changing it to look like '/' minus the quotes. from there you can see some more folders in particular one which says media. click on it. you should be able to see a couple more folders one which should say somehting like sda1. 
If not just click on each until you find which is you LaCie drive. Whatever you get in the url bar when you are in your drive you should put in place of   /media/LaCie_USD_Drive

my guess would be to change the second line I had to 
```
sudo chmod 777 -R /media/sda1/
```

and the first line of code I had to 
```
sudo cp /home/yourusername/nameoffile/ /media/sda1
```

of course changing the yourusername part to your actual login name on the computer. and the nameoffile bit to the name of what ever you want to copy.
this bit /home/yourusername/ says that you are in your home folder. So if you have a folder in there which you want to copy you just need to put the name of the folder in place of the nameoffile bit.
If you have a folder inside your home folder like /home/yourname/folder/anotherfolder/ then that is what you can put there to copy it. Its a good idea to try and understand whats going on and having a mental picture of where everything is. 

I think that makes sense. I hope I havent confused you.

---

### Post by daveymannion on 2006-09-21
hi there, i am trying to write to an external usb drive also but it wont allow it saying i have no the correct privalages oor some shit to that effect. did you find out? maybe you can help me?

davey

---

### Post by Shigglyboo on 2006-09-21
you'll have to learn to use terminal to move files.  I gave up.  I'm running windows XP.  the only nice thing about it is that bit torrent is running 100 times faster and I get full screen youtube and it's in sync.  my only real beef with linux (besides not being able to run any mainstream software like ableton live, cakewalk sonar, VST plugins, and EZ Generator which I used to build my website [www.wesleydysart.com](www.wesleydysart.com) )was the lack of sync with online video streaming ( i tried every player and every codec, I'm sure there's some sort of fix out there ) and bit torrent finds 100's of peers where before it was finding less than 10.  

so yeah.  I just lost the data I wanted to backup.  too lazy to learn how to transfer files in terminal....  I like my gui, I like clicking and dragging.  what can I say?  

oh.  and I miss my fortune telling fish.  can you get that for windows?  and that ugly start menu button... geez.  

but gotta do what you gotta do right?

-wes

---

