---
title: "Addind/Removing Repositories"
date: 2005-12-06
forum: General Help
---

### Post by Seinfeld on 2005-12-06
Hello All.

First, a warm applause to Breezy:KS ..
I have something confusing me with adding/removing repositories from synaptic.
I noticed that when removing a repository from Synaptic (Settings > Repositories) menu, the repository server totally disappears from /etc/apt/source.list file. **Sould it only be commented out ?? **
When I do add, I cannot find the removed one.. That made me re-install again and first thing back up source.list just in case..
I really appreciate your detailed explanation :confused: 

Thanks a lot

---

### Post by MakarX on 2005-12-06
Well, If you want to keep a repository, why get rid of it? Actually, Why get rid of a repositor at all? It doesnt really take up much room..

---

### Post by aysiu on 2005-12-06
You know, I haven't tried that in Ubuntu.
I know in Mepis, when you uncheck a repository, it simply comments it out in the /etc/apt/sources.list.

Well... I tend to edit the sources.list manually--it gives you total control. You want a comment, you can put the # in yourself and know it's there.

---

### Post by BLTicklemonster on 2005-12-06
Here's a neat trick, though I'm sure it's overboard...


Right click on your desktop, and click on create launcher.

Name it Repository.

Go down to where it says command: and put this in

```
sudo gedit /etc/apt/sources.list
```

and check run in terminal. (yeah, pick an icon if you'd like) Now click ok.


Now you can click it, enter your password and be at your repository list immediately. Now click the link in aysiu's sig about repositories, and copy and paste the one pertinent to you in a text document, and save it in /home/yourname/ as repository1 or repositoryaysiu or something unique. Now every time you are called upon to change your repositories, you can start saving them the same way in your /home/yourname/ directory as a different name, but make sure it's a name that will tell you what it is, then you can just copy and paste them into sources.list (that launcher we just made) any time you want. 

I also made one for /boot/grub/whatever when I was working on getting my machine to dual boot and was having to go edit that file endlessly.

Maybe an easier way to do this, but it's easy for me to do it this way.

---

### Post by Seinfeld on 2005-12-06
Hey aysiu...

What a coincidence :razz: 
I posed my question because in fact, I am using MEPIS too :p YEPP..exactly, I am sure that when we do so on MEPIS, it only comments the repository. 
Don't know may it is different here, however I do not really know how it completely delete the repo??. Anyways I will be on the safe side and edit /etc/apt/sources.list manually.. But if you want to try it, do not forget to back the file up :rolleyes: 

Thanks to all for the replies, they are really helpful 

Cheers ;)

---

### Post by korami on 2005-12-07
[QUOTE=Seinfeld]Hello All.

First, a warm applause to Breezy:KS ..
I have something confusing me with adding/removing repositories from synaptic.
I noticed that when removing a repository from Synaptic (Settings > Repositories) menu, the repository server totally disappears from /etc/apt/source.list file. **Sould it only be commented out ?? **
When I do add, I cannot find the removed one.. That made me re-install again and first thing back up source.list just in case..
I really appreciate your detailed explanation :confused: 

Thanks a lot[/QUOTE]


well as far as I can remember (I'm at work right now so I can't verify it) there is an option in Synaptic that, if checked, will display in the repository list also the disabled repositories. In this case, you will see a check-box in front of each repository. Ticking and unticking the check-box does exactly what you are looking for: enabling or disabling a repository.

---

