---
title: "Newbie needs help installing application."
date: 2006-06-01
forum: Desktop Environments
---

### Post by pubwho on 2006-06-01
Hi, I'm new to Linux.

Can anyone point me in the right direction installing Editpad?

The file is located here...

[http://www.editpadpro.com/linux.html](http://www.editpadpro.com/linux.html)

(SetupEditPadLiteFull)

The help file says type the following in to a terminal...

./SetupEditPadLite

That doesn't do anything

I tried

./SetupEditPadLiteFull

That didn't work

I tried double clicking it, still no luck

Then I tried

install SetupEditPadLiteLinuxFull editpad

All that seemed to do was make a second copy called editpad

That's about all I could think of.

Has anyone got any advice?

---

### Post by kingbilly on 2006-06-01
I managed to install EditPad in just a couple minutes. 

I am not sure how much you know about linux yet so i'm going to start very basic :cool: because we want to make this work for you asap!

1) Download the file to your desktop
[COLOR="DarkOrange"]EditPadLiteLinuxFull.tar.gz[/COLOR]

2) Make a temporary folder on your desktop to extract the .tar package.
I would name it editpad.

3) Move the EditPadLiteLinuxFull.tar.gz file into the new folder.

4) Time to extract the .tar package.  You can browse to the new folder and right-click then choose Extract Here.

5) Open the terminal and navigate to your new folder.  It should be located at /home/username/Desktop/editpad.  If you don't know how to move to that folder in the terminal, use this command:

[COLOR="SeaGreen"]cd /home/username/Desktop/editpad[/COLOR]

Replacing username with your username

6) When you are in the folder, run this command to start the install:

[COLOR="SeaGreen"] ./SetupEditPadLiteLinuxFull[/COLOR]

and you will be prompted to choose where to install EditPad.  If you hit enter, it will default the installation to ~/editpad which will be a newly created folder in your home directory.

7) With the installation complete, test it out to make sure it runs:
/home/username/directoryyouchosetoinstall/editpad

for me this was

/home/richard/editpad/editpad 

so if you did the default destination you can just change my name to your username.

8) If it works you can delete the editpad folder on your desktop.  You may want to make a launcher for this program if you don't want to type it into the terminal each time you run it.  Otherwise you should be in business at this point.:-D

To add a custom application launcher right-click on a panel where you would like to put it. 
Choose Add To Panel...
Then the Custom Application Launcher (Or Press Alt + L)
You then enter a name you would like as well as any comments.  Most important, is the command.
It will be /home/username/editpad/editpad  or whatever you chose personally for the destination.  It is the same command that you ran in the terminal to get the program to run.  Choose an icon if you want and you are all set!

For any future help come back to these forums, live chat on the [Ubuntu IRC channel]("http://www.ubuntu.com/community/irc"), and feel free to contact me on aol instant messenger, my screenname is takeyurpants0ff - that is a zero.

Good luck with your start in linux & Ubuntu!

---

### Post by pubwho on 2006-06-01
Thanks for your help.

When I attempt stage 6, I get the following error...

ubuntu@ubuntu:~/Desktop/editpad$ ./SetupEditPadLiteLinuxFull
Unable to open source package /cow/home/ubuntu/Desktop/editpad/SetupEditPadLiteLinuxFull

---

### Post by kingbilly on 2006-06-01
I redid the steps since I did it a different way then I told you to.  This was so you didn't have to use the Archive Manager.  I forgot that when you right click and choose extract here it puts the files in yet a new folder called [COLOR="Blue"]EditPadLiteLinuxFull.tar.gz_FILES[/COLOR]
](*,)  My apologies.

To get around this, (choose A or B, but not both)
[COLOR="Red"]A)[/COLOR] Copy the files in this folder to it's parent folder.
If you can do it graphically through the desktop using cut and paste, do that, or 
if you are still in the /Desktop/editpad folder in the terminal, run this command

[COLOR="SeaGreen"]cp ./EditPadLiteLinuxFull.tar.gz_FILES/SetupEditPadLiteLinuxFull SetupEditPadLiteLinuxFull[/COLOR]

This will copy the install file back to the parent directory.
Then proceed from step 6 again.

or


[COLOR="Red"]B)[/COLOR] Another option is to navigate to the EditPadLiteLinuxFull.tar.gz_FILES folder and run step 6 from there.

[COLOR="SeaGreen"]cd /cow/home/ubuntu/Desktop/editpad/EditPadLiteLinuxFull.tar.gz_FILES/[/COLOR]

 Let me know if i need to be more descript on which files to move, and also if there are any error messages besides "Unable to open souce package" if you still have problems.

_rich_

---

### Post by pubwho on 2006-06-01
Thanks again for your help.

When I tried previously I figured it wasn't finding the file so I moved it.

I've re-run the steps from scratch again, deleting all files and re-downloading the setup.

Here's the transcript of my terminal session...

ubuntu@ubuntu:~$ cd /cow/home/ubuntu/Desktop/editpad/EditPadLiteLinuxFull.tar.gz_FILES/
bash: cd: /cow/home/ubuntu/Desktop/editpad/EditPadLiteLinuxFull.tar.gz_FILES/: No such file or directory
ubuntu@ubuntu:~$ cd /home/ubuntu/Desktop/editpad/EditPadLiteLinuxFull.tar.gz_FILES/
[email]ubuntu@ubuntu:~/Desktop/editpad/EditPadLiteLinuxFull.tar.gz[/email]_FILES$ ls
README.txt  SetupEditPadLiteLinuxFull
[email]ubuntu@ubuntu:~/Desktop/editpad/EditPadLiteLinuxFull.tar.gz[/email]_FILES$ SetupEditPadLiteLinuxFull
bash: SetupEditPadLiteLinuxFull: command not found
[email]ubuntu@ubuntu:~/Desktop/editpad/EditPadLiteLinuxFull.tar.gz[/email]_FILES$ ./SetupEditPadLiteLinuxFull
Unable to open source package /cow/home/ubuntu/Desktop/editpad/EditPadLiteLinuxFull.tar.gz_FILES/SetupEditPadLiteLinuxFull
[email]ubuntu@ubuntu:~/Desktop/editpad/EditPadLiteLinuxFull.tar.gz[/email]_FILES$ ./SetupEditPadLiteLinuxFullnonexistentfile
bash: ./SetupEditPadLiteLinuxFullnonexistentfile: No such file or directory
[email]ubuntu@ubuntu:~/Desktop/editpad/EditPadLiteLinuxFull.tar.gz[/email]_FILES$

---

### Post by kingbilly on 2006-06-02
I'm working on a solution. Sorry it took me a while until I had free time.  I should have it ready in about 10 minutes from now.

---

### Post by pubwho on 2006-06-02
Thanks for your perseverance.

I am running off the Live CD as I don't want to use Ubuntu full time unless I know I can get my core applications to work.

Could the Live CD installation be at fault?

Although I have managed to install everything else fine.

---

### Post by kingbilly on 2006-06-02
That could be why.  I have created a package for you to download.  It has the files that the installer makes, there are 5 or 6.  Try this out.

rm -r /cow/home/ubuntu/editpad
mkdir /cow/home/ubuntu/editpad
cd /cow/home/ubuntu/editpad
wget [http://www.billyandsally.com/editpad2.tar.gz](http://www.billyandsally.com/editpad2.tar.gz)
tar -xvf editpad2.tar.gz
ln -s ./libborqt-6.9.0-qt2.3.so ./libborqt-6.9-qt2.3.so
./editpad


Run those in the terminal.  I edited one of the files to look for the .so files in the directory you will create again.  This should work so give it a try.  And yeah, It could be cause its the live cd, i'm not totally sure because I haven't really worked with it.  But on my desktop and laptop Editpad worked instantly so you could probably check that off your list of core apps.  Hope the other ones work for you too!

---

### Post by kingbilly on 2006-06-02
edit: double post

---

### Post by pubwho on 2006-06-04
I decided to take the jump and assume it was the live cd causing the problem.

I removed windows and installed Ubuntu on to the hard drive yesterday. I installed EditPad today using your original instructions and it installed easily and with no problems.

Thanks very much for your help.

---

