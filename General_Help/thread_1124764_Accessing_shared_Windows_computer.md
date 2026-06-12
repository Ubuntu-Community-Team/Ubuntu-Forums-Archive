---
title: "Accessing shared Windows computer"
date: 2009-04-13
forum: General Help
---

### Post by drummerchrissk on 2009-04-13
I was poking around my Ubuntu system today using Nautilus and under the places sidebar I clicked on Network. It shows two options. 1.) My windows computer in the other room. 2.) An icon that reads Windows Network which ultimately leads to the same place as the first option. A first attempt to access the computer proved to be a success. After entering the username and password for said computer and clicking the 'Remember forever' radio button it brought me to a screen showing three folder icons.

These three folders read 1.) ADMIN$ 2.) C$ 3.) D$

Now I've run into some problems. When I try to open any one of these folders I get a dialog asking to enter the password for the Windows computer. I put in the correct username and password and make sure once again that the 'Remember forever' radio button is selected, but when I hit Connect the window dissappears very briefly then reappears with my Ubuntu username pasted in the Username box, the password box empty again, and the 'Forget password immediately' radio button reselected. I am positive that the username and password I'm attempting to use are both correct so now I'm kind of lost.

My question is if I'm putting in the correct username and password for these folders why won't it let me access them? What am I doing wrong?

Secondly, is there a way to access another Ubuntu computer on my network from my computer? If so, how is this done?

---

### Post by hwttdz on 2009-04-13
Accessing another linux box is easier than accessing a windows box (in my opinion).  You can ssh to pull up a terminal on the other machine (-X will get you graphical forwarding), or use sshfs to pseudo-mount the disk. You'll have to know the ip address of the other machine.  Run ifconfig from the terminal, and you can then 

> ssh [email]username_on_other_machine@othermachine.ip.addres[/email]s
then it will prompt for the password of the user you are connecting as.  

When connecting to the windows box are you sure it's not asking you for your ubuntu username/pass, because connecting to another machine like that might require admin privileges.  

Let us know.

---

### Post by DenysT on 2009-04-13
The shares you are seeing are default administrative shares for administrators in Windows. Even though they are visible they are not accessible by default. You must enable the shares in Windows, but you will be warned about doing so. Until you enable them they are only visible but not accessible.

---

### Post by drummerchrissk on 2009-04-13
>  Re: Accessing shared Windows computer
Accessing another linux box is easier than accessing a windows box (in my opinion). You can ssh to pull up a terminal on the other machine (-X will get you graphical forwarding), or use sshfs to pseudo-mount the disk. You'll have to know the ip address of the other machine. Run ifconfig from the terminal, and you can then

> ssh [email]username_on_other_machine@othermachine.ip.addres[/email]s
then it will prompt for the password of the user you are connecting as.

When connecting to the windows box are you sure it's not asking you for your ubuntu username/pass, because connecting to another machine like that might require admin privileges.

Let us know.

Everything you just said about connecting to the Linux computer went right over my head. I'm really inexperienced as far as things such as that go. I'm reading more and more about it everyday. But if you care to explain how to get this working in great detail then feel free. I'll listen and follow direction. If it's a bit too much, eh don't even worry about it.  :) 

I did try my Ubuntu username and password. It did not work. I think DenysT has the right idea about the shared folders and such. Thanks to both of you for your quick replys. :)

---

### Post by hwttdz on 2009-04-13
Ok so we have 2 machines, and a user on each machine.  Let's call machine1 earth, and machine2 mars.  If we're logged in to earth as bugs and we want to connect to mars as martian what we'll see at the prompt is something like

bugs@earth > 

and we're going to want to ask the machine to log in to a different machine as a different user, the syntax for this is user@machine.  So in our example if we wanted to connect to mars as martian we'd do

bugs@earth > ssh martian@mars

mars (the machine) then asks us for martians password.  Once we give the password we see.

martian@mars > 

Success.  However this is complicated slightly because your computer (earth) doesn't know where the other computer (mars) is located.  So it needs an address, which comes in the form of XXX.XXX.XXX.XXX.  And to get this address you need to run "ipconfig" from mars, which will tell you the ipaddress of mars, so if the ipaddress is 192.168.100.2 then what you would need to do from earth to go to mars is

bugs@earth > ssh martian@192.168.100.2

If bugs is also a user on mars, you can connect as

bugs@earth > ssh mars  (and the machines will assume you are connecting as the same user)

Of course if you're sitting at earth, and working on mars and you do something like "firefox" you'll get some error about windows forwarding.  ssh communication by default does not support sending the graphics output of one box to another box's monitor, you solve this by feeding the ssh command the -x option.

bugs@earth > ssh -X martian@mars

Finally ssh allows you to pretend that a remote disk is mounted locally.  So you can do anything you want as if it were local.  This is a bit more complicated but fundamentally the same. Suppose you wanted to be able to work on things at mars from earth you'd do

bugs@earth > sshfs martian@mars:/home/martian/ /home/bugs/local_mars/

This mounts martian's home directory on mars in a folder named local_mars in bug's home directory on earth.  

Also take a look at "man ssh" and "man sshfs", if you get an error about either you may have to do "sudo apt-get install programname".  To install the program.  I don't know if the ssh server is installed by default, so you'd need to install that on any machine you want to connect to so

martian@mars > sudo apt-get install ssh

---

### Post by drummerchrissk on 2009-04-14
Ok. I read through your post, followed all directions, and figured it out in all of about 20 minutes. Thank you so much. I have only 3 more questions.

1.) Will your previous post work on a Windows computer on the network? (keeping in mind that on both Ubuntu computers involved i had to install ssh server and sshfs and naturally, this being a Windows computer I want to connect to, both ssh server and sshfs will not be available)

2.) Say I've mounted a location using the sshfs command you told me about.  Is it all possible to save a file to this location from earth, and then physically log into mars and be able to read and/or write to said file?

3.) I'm having some issues with the Remote Desktop function.  Everytime I type in the command 'vinagre machine-name:0' it opens the Remote Desktop window and then gives me a dialog that reads 'Connection to host "machine-name:5900" was closed.' Am I missing something here? A package that needs downloaded? Something?

---

### Post by hwttdz on 2009-04-14
1.) Will your previous post work on a Windows computer on the network? (keeping in mind that on both Ubuntu computers involved i had to install ssh server and sshfs and naturally, this being a Windows computer I want to connect to, both ssh server and sshfs will not be available)

Connecting from a windows computer to a linux machine is very easy.  All you need is an ssh client, putty is a very nice free one, the ssh client will ask you for the username and password of the account on the linux box, and then it will give you a prompt on that machine.  

I know there are two possibilities for the other direction
1) telnet - included in windows by default (nothing to install)
2) ssh-server - you'd need to find one and install it
But I don't know enough to be terribly helpful. 

2.) Say I've mounted a location using the sshfs command you told me about. Is it all possible to save a file to this location from earth, and then physically log into mars and be able to read and/or write to said file?

Yup, that's exactly what happens.  To give you an idea I often use sshfs to mount a remote drive locally, then use my local graphical editor to edit the file.  Then compile and run the program through ssh.  It's kind of like working on both machines at once.  

3.) I'm having some issues with the Remote Desktop function. Everytime I type in the command 'vinagre machine-name:0' it opens the Remote Desktop window and then gives me a dialog that reads 'Connection to host "machine-name:5900" was closed.' Am I missing something here? A package that needs downloaded? Something?

I believe this is for vnc desktop forwarding.  You need to make sure that there is a vnc server running on the box you are connecting to and that the necessary ports on that machine are open.  If you give a bit more information about the machine you are connecting from and to, as well as what server you have installed I might be able to help.  Google "vnc server windows" or look in synaptic.

---

### Post by drummerchrissk on 2009-04-14
When I mount a local drive and get into Nautilus to have a look, I see all of my files. However if I try to save something to this location it tells me I don't have the space. Looking down at my status bar, I see that I have o bytes of free space. Yet when I physically log on to my second computer, it tells me I have 118.3 GB of free space.

You talked about needing a vnc server running on the computers. Is this made available through Synaptic Package Manager? Exactly what information about my system would you need?

---

### Post by Disorder on 2009-04-14
I'm having the same problem with 8.11 Kubuntu

I went into dolphin > network > and then added a network folder

Typed in my winodws un/pw and was able to browse to my shared windows drive(NTFS) 

I browse to my music folder and add songs to Amarok but when I play them I get:

No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
smb://joseph@10.0.0.114/E/Music/12 Hour Turn/Bend Break Spill/01-I To Had Potential .mp3

---

### Post by hwttdz on 2009-04-14
Disorder, go ahead and edit out your ip address, that's considered private info.  

Addressing the no space issue with sshfs, this is often a permissions issue, having to do with insufficient write permissions.  With sshfs I have some options set as 

sshfs martian@mars:/home/martian/ /home/bugs/mars_local/ -o uid=1000,gid=10;

namely the -o.

RE: vnc server.  Are you trying to desktop forward from a windows box to your linux box?  The machine which is having its desktop forwarded needs to be running a vnc server.  

RE: no suitable plugin, do other mp3 files play?  It seems to be a complaint about not having a decoder.  Additionally, this is a smb not sshfs.  

Finally these questions are moving further away from the original topic.  Perhaps a new thread should be started.

---

### Post by drummerchrissk on 2009-04-14
No. I am trying to forward the desktop from one Ubuntu system to another. I actually got it to work but the particular system I'm trying to forward from has multiple users. I could only forward this computers desktop if I was logged into my own account on the computer. Noone elses accounts worked.

You said that -o might fix my permissions? Am I looking at using the same information you had after the -o, or is that information dependant on something in an individual system

---

