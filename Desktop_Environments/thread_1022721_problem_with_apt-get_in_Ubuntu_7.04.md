---
title: "problem with apt-get in Ubuntu 7.04"
date: 2008-12-27
forum: Desktop Environments
---

### Post by balaji_n on 2008-12-27
Hi All,
Being a linux newbie i just installed Ubuntu 7.04 in my HCL laptop with 256 MB RAM. This forum is of great help to me since i installed it.
Now, the problem is, when i try to install sun jre and issue command in the terminal
```

sudo apt-get install sun-java6-jre

```
it says,
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jre

```
Someone said in this forum earlier, that Ubuntu 7.04 is no longer supported. Is that the reason for the result showing 'couldn't find package'? Or do i have to check anything before running this command. I have internet connectivity in good condition. 
I am afraid, whether my 256 MB RAM can support Ubuntu 8.10 or should i have to move to xubuntu?
Many thanks in advance.

---

### Post by Bucky Ball on 2008-12-27
xubuntu would be a good idea with those specs anyhow and should give better performance. The xfce desktop environment is great and I use xubuntu on more powerful machines I like it that much! But I am not an eye-candy junky.

You could try:

```
sudo apt-get update
```then try again.

Go to:

System->Administration->Software Sources

and confirm you have the correct repositories ticked.

---

### Post by balaji_n on 2008-12-27
Thanks Bucky, I gave the command you mentioned, it loaded some packages yet many gave 404 error as shown below.
```

...
Hit http://ftp.iitm.ac.in feisty-security/universe Packages                    
Hit http://ftp.iitm.ac.in feisty-security/multiverse Packages                  
Err http://ftp.iitm.ac.in feisty/main Packages                                 
  404 Not Found
Err http://ftp.iitm.ac.in feisty/restricted Packages                           
  404 Not Found
Err http://ftp.iitm.ac.in feisty/restricted Sources                            
  404 Not Found
...
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
i have connected to the nearest university ftp server. Hope the packages for fiesty is no longer available :( can i change some other server where fiesty packages still available for download?

---

### Post by Bucky Ball on 2008-12-27
Ah ha. 7.04 was Gutsy. Try those repositories.

* Update, scratch that. It was Feisty, sorry. My mistake. :)

Try connecting to the 'main' server and see if that works. The Feisty repositories may not be supported on your current uni server (outdated). You should be able to test this with the 'sudo apt-get update' command. When that works, you're in business.

Not sure if of any help, but I also came across this:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

End of the day, I would still go for Xubuntu 8.04, which is supported for about another four and a half years (about) and will give better performance with your machine. You will probably find the Gnome or KDE environments a tad sluggish. Openbox or xfce should speed things up considerably.

---

### Post by namdung on 2008-12-27
Balaji, why are u still stuck with ancient 7.04? Is there any specific reason as so many of us already advised you on this even on previous occasions?

Pls upgrade immediately to Hardy Heron 8.04 LTS even though Intrepid Ibex 8.10 is available.

Next version of Hardy 8.04.2 is out on 1/1/2009.

Xubuntu is recommended for lower hardware specs.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

sun-java6-jre is not available for 7.04, unless u directly download and install from the sun website.

---

### Post by theozzlives on 2008-12-27
7.04 is past it's end of life... no repositories

---

### Post by theozzlives on 2008-12-27
> **balaji_n said:**
> Hi All,
Being a linux newbie i just installed Ubuntu 7.04 in my HCL laptop with 256 MB RAM. This forum is of great help to me since i installed it.
Now, the problem is, when i try to install sun jre and issue command in the terminal
```

sudo apt-get install sun-java6-jre

```
it says,
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jre

```
Someone said in this forum earlier, that Ubuntu 7.04 is no longer supported. Is that the reason for the result showing 'couldn't find package'? Or do i have to check anything before running this command. I have internet connectivity in good condition. 
I am afraid, whether my 256 MB RAM can support Ubuntu 8.10 or should i have to move to xubuntu?
Many thanks in advance.

I have 2 computers with 256 MB RAM running 8.10

---

### Post by balaji_n on 2008-12-27
one question, might be silly!
i have installed this Ubuntu Feisty (Thanks Bucky :) Now i am spelling it right) into a single partition taking whole of my 40 GB hard disk. 

I have stored all of my files in /home/balaji/Desktop which i can take backup. No problem in it. All i wanted to know is, Can i straightly upgrade it to Hardy without formatting the disk? Pls provide any links for this kind of installation.
Many thanks.

---

### Post by Bucky Ball on 2008-12-27
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

All you need to know. A clean install after backup of your precious data sounds like the go as you are skipping 7.10 to get to 8.04 and this is not advised. The other thing is that if you go for Xubuntu, you are running Ubuntu therefore an upgrade (as such) wouldn't be possible.

---

