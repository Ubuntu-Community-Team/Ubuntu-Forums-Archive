---
title: "Home folder question"
date: 2006-01-03
forum: Desktop Environments
---

### Post by rickyjones on 2006-01-03
Hey all,

I'm a new user to Ubuntu, but I'm loving every minute of it. I have it installed on my notebook, and getting it installed was the first step on my way to moving to a fully opensource platform. However, I've run into a small issue.

I run a mixed network of Windows and Linux. I wish to move all my primary computer use over to Linux (mainly Ubuntu on my notebook), however I need to have access to a centralized "My Documents" from both Linux and Windows. My idea is to throw a 120GB drive into my server machine and keep it on 24/7. This solves the problem with my desktop machine, 'cause I can just map the drive over the network. However, how can I accomplish this on the client end for my notebook? I assume I'll have to do an SMB mount - but I've never worked with this before. Also, the documents and information must be with me 24/7, which means having a copy locally on the notebook which is synced to the network, yet also allowing my desktop to interact with the network and reflect the changes to my local repository.

Any help in this area is appreciated (and I know I'm asking for a lot.)

Thanks!

-Richard

---

### Post by bunced on 2006-01-03
[http://www.awprofessional.com/articles/article.asp?p=100666&rl=1](http://www.awprofessional.com/articles/article.asp?p=100666&rl=1)

Note: rsync should be installed on Breezy by default, so you don't need to do the installation stage.It takes you through configuring it in great detail. Any problems, just ask :)

---

### Post by rickyjones on 2006-01-03
This definitely puts me a couple of steps in the right direction, however I have an uneasy feeling... In this scenario, my file setup would be like this:

```

Edmund (notebook) - main file repository
                                    |
                                    |
                                    |
                                    |
Fenthick (desktop)----->  AIRA (server)

```

Fenthick interfaces directly with the file repository on AIRA, while Edmund interfaces with it's local file repository then uses RSYNC to sync the server. Now, what happens when I edit a file on the server from Fenthick? Will the change be propagated to Edmund when I run RSYNC on Edmund?

Thanks!

-Richard

---

### Post by rickyjones on 2006-01-03
Bumping this thread back up since it got buried on the fourth page :(.

If this is unallowed, please let me know. :)

Still looking for ideas/theories on my second question.

Thanks!

-Richard

---

### Post by agds on 2006-01-04
You might be interested to know&#8212;if you didn't already&#8212;that you can right-click the My Documents icon on your Windows desktop to assign it a different path.  Just use the *Move&#8230;* button.

---

### Post by rickyjones on 2006-01-04
[QUOTE=agds]You might be interested to know—if you didn't already—that you can right-click the My Documents icon on your Windows desktop to assign it a different path.  Just use the *Move…* button.[/QUOTE]
Yes, I know that. :) That was my plan for solving the My Documents issue on the desktop. The problem arises when I edit a file on the server from my desktop... will RSYNC propogate the updated file to my notebook when I sync from the notebook?

---

### Post by bunced on 2006-01-04
After doing some research into your problem, I believe that the answer is to actually use some software called Unison, which is a modified form of rsync.

to get this, first do: 
Applications -> Accessories -> Terminal 

type the following and hit enter
```
sudo apt-get install unison unison-gtk
```
when it asks you for a password, enter your user password. When it has finished installing, type
```
unison-gtk
```
and hit enter.

A window will pop up asking you to select a profile or create one. Create a new profile and give it the name 'Sync'

Hit enter

Now double click the sync profile and a window will pop up asking you to check the folder you want to sync. Browse until you find your home directory, or whatever folder you wish to use, then click OK

On the second window, login your preferred method (if your server is *NX, I suggest using ssh) and fill in the details. Now click OK.

A window will probably come up telling you no files were found. Click OK. Then it will begin to sync. Just leave it going - this replicates the changes across both folders - it may take 30 mins +

Now, whenever you want to sync, just fire up unison, select your profile and hit Go. This will sycronise the two sources.

I hope this brief how-to was useful - let me know if you have any problems and I'll try and work them out with you. This is my first ever look at Unison though, so we'll have to puzzle through together.

Blessings,
David

---

### Post by rickyjones on 2006-01-04
UNison huh? I looked at that for a customer once - I liked it's features. :)

Thanks for the recommendation, I think this will do what I need it to do.

-Richard

---

