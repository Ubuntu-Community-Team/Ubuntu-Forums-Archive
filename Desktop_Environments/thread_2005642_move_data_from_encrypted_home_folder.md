---
title: "move data from encrypted home folder??"
date: 2012-06-18
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2012-06-18
Hi all,

I have a problem on my system that is not allowing me to start a desktop session (xfce), even though it accepts my password ok. After I enter my password at the prompt, I get terminal mode only.  I'm running xubuntu, and I can only access my data through the terminal mode. All the other users on the system have no difficulty starting the desktop gui. The user 'art' has an encrypted home folder.

So, I need to figure out how to retrieve my data from the 'art' user repository, and move it into the 'artie' user repository. I figured out how to move the desktop data, so it is safe now. Please note, I don't want to move the entore home folder, just a single file within the home folder.

I need to retrieve one more folder, which is a hidden folder I installed in the home folder called xyz, But, I think the command I'm trying to move the xyz file is incorrect, likely due to my lack of experience using the terminal mode.

Heres the command I was trying to use:

sudo cp -R /home/art/xyz /home/artie/xyz/

Please note, I have the original password for user 'art' and the passphrase. 

Can anyone advise me what I'm doing wrong?? 

TY.

Art

---

### Post by mexicanseaf00d on 2012-06-18
if it is a hidden folder, it will most likely start with a .
like:

```
sudo cp -R /home/art/.xyz /home/artie/.xyz/
```
also, consider using cp -a (preserves attributes, user, group etc) EDIT: nevermind that if you dont want to restore "art"

---

### Post by goodbye-windows(tm) on 2012-06-19
The copy command worked fine, although I do have a new problem. 

After the copy, the xyz folder in the artie folder now belongs to 'root' when I look at the permissions. 

So, I can't copy, move or even examine the contents of the folder.

How do I change the permissions so that the folder has read and write, and so it belongs to 'artie' instead of 'root'?

TY

Art

---

### Post by mexicanseaf00d on 2012-06-19
sudo chown -R artie:artie .artie

(chown -R = change owner including subdirs; artie:artie = user:group)

---

### Post by goodbye-windows(tm) on 2012-06-19
Should I migrate to the home folder, then do the chown command? Or do I execute the command after selecting the artie folder? Or, do I migrate to the xyz folder, then execute the command???

TY.

Art

---

### Post by goodbye-windows(tm) on 2012-06-19
I used the terminal mode to change to the xyz directory, but didn't open it.

I then issued the command, just as you gave it to me.

Here's the results I got.

artie@art-desktop:~$ dir
a7.odt    Desktop    Downloads  Pictures    Templates
xyz    Documents  Music      Public    Videos
artie@art-desktop:~$ cd xyz
artie@art-desktop:~/xyz$ sudo chown -R artie:artie .artie
[sudo] password for artie: 
chown: cannot access `.artie': No such file or directory
artie@art-desktop:~/xyz$     

Is there something missing, such as giving the path to the folder within the chown command? 

TY.

Art

---

### Post by mexicanseaf00d on 2012-06-20
You forgot the DOT in front of the directory. Dot infront means "hidden". Use ls -a to list directory including 'dotfiles' = hidden stuff. 

your folder is at */home/artie/.xyz* if you copied it like in an earlier posting.

If you provide the full path, like```
 sudo chown -R artie:artie /home/artie/.xyz
``` it does not matter where your current working directory is (where you 'are' at the moment').

This is quite helpful [http://divajutta.com/doctormo/learning/command-line/cheat-sheet.pdf](http://divajutta.com/doctormo/learning/command-line/cheat-sheet.pdf) (from [DoctorMo's Blog]("http://doctormo.org/2009/07/15/ubuntu-system-admin-class-command-line-basics/"))

---

### Post by goodbye-windows(tm) on 2012-06-20
I'll have a look at DoctorMo's blog. 

I actually didn't leave out the dot, when I copied the folder from the original directory (which was the 'art' directory), I renamed the file to 'xyz'. So, now that the file is in artie, it is no longer hidden.

There is an interesting oddity however...perhaps it's nothing. But, whenever I try to change the ownership, the computer asks me for artie's password. If the folder is only available to 'root', shouldn't it be asking for art's password (art is the superuser's  user name).

So, I ran the command as follows, using cut and paste so as not to copy it improperly........

sudo chown -R artie:artie /home/artie/xyz

After I run that command, I am prompted for artie's password. When I enter arties password and hit enter, there is a brief delay, and the terminal prompt appears, just as it should. But, when I look at the xyz folder, the X still shows, just as it always does.

When I looked at the permissions though, I could see they were changed, even though the X was still showing on that folder. I noticed there was a prompt asking me if I wanted to restore the folder to 'normal' permissions. I told it to do so. In  a few short seconds, the X disappeared and I had full access to the folder!!!

So, it looks like the problem is solved.

I want to thank you for sticking with me. There are so many things about linux that are troublesome and reading the docs doesn't always help. 

I'm still going to read DoctorMo's pdf file on the subject.

Regards,

Art

---

### Post by mexicanseaf00d on 2012-06-20
Glad it worked in the end.

There are a lot of guides like the mentioned blog, I just gave you this link because it was one of first i found.

That bash-cheat sheet is useful though, there are lots like that out there

---

