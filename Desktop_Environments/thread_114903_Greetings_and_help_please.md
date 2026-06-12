---
title: "Greetings and help please"
date: 2006-01-09
forum: Desktop Environments
---

### Post by ktb973 on 2006-01-09
First off I'd like to say hello.  I am new to the forum and ubuntu and looking forward to the experience.  

I come from the point and click windows and mac world but linux has always seemed interesting to me so I thought ubuntu sounded like a perfect way to get my feet wet. 
I also knew that I was going to be getting into the CLI environment but I am eager to  learn.  

My problem is that the first thing I tried to do was to update firefox to 1.5.  I went to the FirefoxNewVersion Wiki and followed all of the instructions  but I'm still having trouble.  When i try to execute sudo cp firefox-1.5.tar.gz/opt/ command It gives me the following message. 

cp: missing destination file

Oh and by the way I have actually downloaded firefox-1.5.tar.gz and it is on my desktop.  

Missing destination file to me means that the opt file is not there, however I can see it in the file browser so I must be misunderstaning destination file or I have a setting wrong.  As I said before I am new to the linux world but am very eager to learn.  

Any help would be greatly appreciated.

---

### Post by gabspeck on 2006-01-09
The only thing you did wrong was forgetting to add a space between firefox-1.5.tar.gz and /opt/ ;) It's got be like this:

sudo cp firefox-1.5.tar.gz /opt/

---

### Post by ktb973 on 2006-01-09
Yes I originally tried the command you suggest however I get this problem with that command. 

cp: cannot stat `firefox-1.5.tar.gz' : No such file or directory

So I really don't understand that one, considering I can see it right there on my desktop.  I even redownloaded it to make sure there was nothing wrong with the file.  Is there possibly something wrong with it being on the desktop?  

Again thanks for any help.

---

### Post by Randomskk on 2006-01-09
Once you've loaded a terminal, you're in /home/user, but your desktop is /home/user/Desktop (note capital D), and if the file is there then you'll need to cd (change directory) there:
cd Desktop (from /home/user) or cd ~/Desktop (from anywhere).

edit: use "ls" or "dir" to list what files exist at where the command line is, always useful :)

---

### Post by ktb973 on 2006-01-09
Thank you very much for the help.  Worked perfectly.  Been trying to figure it out on my own all weekend.  That's a valuable lesson.  I knew it had something to do with where I was looking but didn't really know about changing directories and such.  

Again thanks for the help.  I'm sure I'll be back soon with another newbie question.

---

