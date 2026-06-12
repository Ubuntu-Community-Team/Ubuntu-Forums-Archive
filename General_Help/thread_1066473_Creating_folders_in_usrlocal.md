---
title: "Creating folders in /usr/local"
date: 2009-02-10
forum: General Help
---

### Post by Sojurner on 2009-02-10
How can i gain Write access to the /usr/local direcotry. When i partitioned my drives it had been quite some time since i used linux and i was thinking /usr/local was my local users directory when infact it was /home. I guess i made a boo boo. 

Well anyway i cant log into root because the install never prompted me for a password and it seems that root is the only one who can write to this directory. I have 160 gigs of space i cant use now.

Basically all i want to do is create one folder to store stuff in and now i cant. 

1. how can i actually log in as root and add user account to the permissions so i can write to it

2. Whats the password for root since it never prompted me. I have tried both (blank) and my regular user password. Neither Work

ANY HELP IS GREATLY APPRECIATED.

---

### Post by snova on 2009-02-10
You cannot log in as root; see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Even so, you shouldn't be writing to /usr/local at all. That directory is meant for programs you install yourself.

---

### Post by personjerry on 2009-02-10
you CAN log in as root in 'recovery mode' ( all it is is just root, really.). otherwise, the sudo command allows the command passed to it to execute as root, while the su command
allows you to use root for as long as you want.

---

### Post by Sojurner on 2009-02-10
i am aware of what /usr/local is for. I had a brain maulfunction when i partitiond my drives and put way too much space there. I want to be able to create a folder and link it to my desktop for storage only. I wont be installing 160 gigs worth of software and want to regain some of that space and use it for storage. 

I am very aware of sudo since i have used it several times to get drivers installed recently. this however is not the answer to my problems since i need access to the root account to add my current user account to the group that owns /usr/local

If there is another way to do this i would love to hear it. 

All i want is to be able to create a single folder in usr/local so i can use it for storage since i have way to much space dedicated to it.

---

### Post by redseventyseven on 2009-02-10
snova is right, you shouldn't be writing things there. However, I accept that that doesn't help you in getting back your 160GB of space.

You should be able to free up some of space by repartitioning your drives - though I would suggest backing up your files first!

Here are a couple of sites that may be able to help you:

[http://www.64bitjungle.com/tech/repartitioning-ubuntu/](http://www.64bitjungle.com/tech/repartitioning-ubuntu/)
[http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/](http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/)

And let me say it again - back up your important files first!

---

### Post by Sojurner on 2009-02-10
yes but if i repartition my drives i will have to re install my OS and everything i have done so far.

I understand that i shouldnt be writing there but if i choose to then big deal right?

I want to make a folder for storage of stuff. Im not going to repartition and reinstall everything. I know you people dont want anybody to log in as root but if thast what i need to do to achieve my goal then help me. 

Im not trying to be an *** but if your not going to help me then please dont post.

Writing to /usr/local wont mess anything up even tho i shouldnt be writing there. An extra directory that just holds stuff wont cause a problem.

---

### Post by personjerry on 2009-02-10
redseventyseven: his problem, stated, is that he's put the user folders in the wrong directory.


Your answer, if you don't like sudo, is su. open a terminal, type su and press enter. type root password. voilà, basically logged in as root. beware, with great power comes great responsibility!

---

### Post by Sojurner on 2009-02-10
well thanks personjerry but i knew about the SU command already from my previous time in linux years ago 

however my problem is that i dont know the default password. I have read all over that its the one i use for my regular user account but that does not work..I have also tried no password seeing as how i didnt assign one when i installed ubuntu

Do i have to unlock it and if so how do i do that

---

### Post by personjerry on 2009-02-10
lol you couldve made that clearer... type sudo passwd in a terminal, and this allows you to change root password.

---

### Post by Sojurner on 2009-02-10
sorry i thought i did in my original post.

Well i just did that and made my root password blah blah blah.. and so now i have SU Root'd myself into root

my system still is denying access to /usr/local where i need to make a directory and add write permissions for my other user..

can this even be done?

---

### Post by snova on 2009-02-10
> **personjerry said:**
> Your answer, if you don't like sudo, is su. open a terminal, type su and press enter. type root password. voilà, basically logged in as root. beware, with great power comes great responsibility!

Except you can't log in as root, so that won't work. ;)

All right, I don't think it's too hard.

Press Alt-F2, type in:

```
gksudo nautilus
```

To get a file browser with full administrative rights.

Navigate to /usr/local, and create a directory there. Right click on it, click Properties, then to the Permissions tab. Click on the Owner menu and select your own user.

---

### Post by Sojurner on 2009-02-10
wow perfect thanx ...thats all i needed... i didnt really want to go the root way but thats the only way i knew about..

this worked fine

---

### Post by personjerry on 2009-02-10
sudo nautilus does much the same. basically, since you can use sudo, you can change root passwd or mkdir... and that's what you needed, right? then a line of sudo chown <user> gives it to you, so you can do further modification from the comfort of your account.

---

### Post by Sojurner on 2009-02-10
thanks guys. i really appreciate it. i have alot to remember. this is stuff i used to know but its all sounding pretty familiar now.

---

### Post by dcstar on 2009-02-11
> **Sojurner said:**
> 
.........
I understand that i shouldnt be writing there but if i choose to then big deal right?

I want to make a folder for storage of stuff. Im not going to repartition and reinstall everything. I know you people dont want anybody to log in as root but if thast what i need to do to achieve my goal then help me. 
........
Writing to /usr/local wont mess anything up even tho i shouldnt be writing there. An extra directory that just holds stuff wont cause a problem.

You can make **ANY** folder name you like, so don't use system folders just because the name is "convenient".

System folders are assumed to be the property of and under total control of the system, so **it** can do what **it** likes to them and their contents.

If anyone puts their data in a system folder because they are basically too lazy to do something like "mkdir /my-data" (or whatever) and use that then they are fools to themselves and a burden to others (as posts in this forum unfortunately prove on a regular basis).

---

