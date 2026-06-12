---
title: "A few questions from a newby"
date: 2010-10-16
forum: Desktop Environments
---

### Post by Downloaded7 on 2010-10-16
Hey everyone,

I just installed Ubuntu 10.4 on my desktop (custom built) and everything is working fine for the most part except for a few little things.  I'll get right to the point.

1.  I installed 10.4 from a CD I burned a few months ago, is there a way to upgrade natively to the newest version, did it do it automatically when I updated my drivers?

2.  I've been messing around with trying to get my desktop to look prettier than the default settings and I've turned on the most visually appealing setting in the appearance tab of the system menu but I can't get the desktop cube to work no matter what I do.  I've been trying the instructions posted here: [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml) and now I'm worried I may have messed something up.

3.  For some reason I'm also having trouble setting up my mail client...  I've entered all the information I think is necessary but when I click send/receive nothing really happens.  The chat client works fine, though.

4.  I have Ubuntu on a 17GB partition of my HDD and all of my music is on the other partition with Windows 7 on it.  Is there a way  can access my music in Ubuntu on the other partition?

5.  This isn't really a complaint but if you guys can think of any useful apps/tips for me that would be really great.  I just want to use Ubuntu as my work OS so I'm not distracted by all the games on my Windows partition.

Thanks!

---

### Post by inobe on 2010-10-16
for #1

your good with 10.04 for now.

for #4

click places, cick the partition you wish to access, if you know the partition size' go by that.

for #5

what type of programs did you use in windows, multimedia, office, animation, photo editing ?

3 out of five questions for now, someone will help with the unanswered questions

---

### Post by ankspo71 on 2010-10-16
Hi,
That link you used is pretty old in terms of Ubuntu years. I'm not sure if it would have harmed your 3D effects though. I think it would be best to disable/remove the repository you added (if you added it) and check for updates. 

As far as getting the Compiz Cube to work.
Make sure that you have these installed:
compiz-fusion-plugins-extra (optional, offers more 3D effects to choose from)
compiz-fusion-plugins-main
compizconfig-settings-manager (to enable and configure the cube and other 3D effects)

When you are sure they are installed, make sure your 3D effects are enabled by going to System > Preferences > Appearances. Click on the 
Visual Effects tab and choose either Normal or Extra.

Now go to System > Preferences > CompizConfig Settings Manager.
Enable the following: Desktop Cube, Rotate Cube, and Cube Reflection and Deformation.

Now to test if the cube works, you can use these keyboard shortcuts:
Ctrl + Alt and drag the desktop in any direction to manually rotate the cube.
Ctrl + Alt plus Left or Right arrow keys to flip through the desktops using the cube.

After you find out the cube works, you can go back and configure those Cube related items that you just enabled.

---

Be sure that your workspace switcher is configured either as 1x3 (at least), 1x4, 1x5, etc. The Compiz Cube doesn't work very well if your workspace arrangement has multiple rows, like 2x2, 2x3, 3x4, etc.

Also, if this doesn't help. It could be that the compiz settings got messed up (it sometimes happens), so if it doesn't work, delete or rename the compiz settings directory located at: /home/yourname/.config/compiz.
The compiz directory is a hidden directory because of the period in front of the folder name. So when you open your home folder, press Ctrl + H to reveal hidden files and folders. After you delete or rename that compiz settings folder, go back and do the above steps again.

Hope this helps.

---

### Post by Downloaded7 on 2010-10-16
Great!  Compiz is now fully functional and I finally have my desktop cube.  To answer your question, I use my Windows partition for gaming and music and (up until now) work.  I'd just like Ubuntu to be a snappy OS that's able to satisfy all of my work needs.  I'm just a college student right now so that means looking stuff up online and writing papers, etc.  

It doesn't seem that I can access the music stored on my Windows partition.  When I go to "places" the only options other than "pictures", "music", etc. are "computer", "System Reserved", and "Floppy Drive".  None of which have my windows files on them...  At least I don't think so.  If I go to the computer there is also a "file system" HD location but I don't see anything of use there.  I think I'm just not sure what I'm looking at...  The files are probably all there somewhere.

As far as the mail client goes, I must have just messed up the setup.  Is there a way I can just start over?

Also, what's a good RSS Reader for Ubuntu?  If I could have news updates pop up on my desktop like chat notifications, that would be awesome!

---

