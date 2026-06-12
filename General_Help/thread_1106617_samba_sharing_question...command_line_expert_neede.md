---
title: "samba sharing question...command line expert needed"
date: 2009-03-25
forum: General Help
---

### Post by caperpc on 2009-03-25
hello all
need help please...i have rtfm many times and googled the crap out of this one with no answer.

here is my sitch

i want to set up a file server in my office...attach a huge usb drive
done. (which i had to force mount...grrrr)

install samba...configure the conf file and create user in smbpasswd
done.

now i want to share a folder on this usb drive but have no gui...i know that i can right click on a folder choose sharing options, click sharing blah blah. if i had a gui of course..but dont want to install one unless i really have to.

there is got to be a way command line, ssh whatever to indicate or activate sharing on a particular folder.

Please help if you can 
thanks a million
ubuntu rocks
windows sucks
lol

---

### Post by evilaim on 2009-03-25
When you setup your samba user, set the user's home dir to the folder you'd like to share and presto.

---

### Post by caperpc on 2009-03-25
thats sounds awesome
is there special syntax when creating the user to specify the folder
sudo smbpasswd -a "user" is what i used...anything i should add?

---

### Post by Kaik541 on 2009-03-25
Besides the obvious nautilus plugin which you don't want, the easiest thing to do is open your favorite text editor (nano, gedit) and add the line [should be done with gksudo/sudo]

usershare owner only = False

under the [global] section of the /etc/samba/smb.conf file. Not sure how "safe" this really is, but if you trust the people on your network it shouldn't be a real problem.

Then scroll to the bottom under Share Definitions and add something

[Example]
   comment = Example Drive
   browseable = yes
   path = /path/to/drive
   read only = (whatever you want to be true)
   guest ok = (you choose)

if you read the smb.conf files there are example explanations of everything including the "create mask" and "directory mask" options.

After setting it to what you want either restart (guaranteed) or do 

sudo /etc/init.d/samba restart

(I occasionally find the above isn't immediately obvious when browsing network servers)

---

### Post by capscrew on 2009-03-25
> Install samba...configure the conf file and create user in smbpasswd
done.

You add the shares in the /etc/samba/smb.conf file!

As in:```

#======================= Share Definitions =======================
# Basic Share for the network

[Share]
        comment = Public Share
        path = /<wherever>/share
        browseable = yes

        guest ok = yes
        writeable = yes
        create mask = 0775
        force create mode = 3775
        directory mask = 3775


```

---

### Post by caperpc on 2009-03-26
Solved guys....thanks a million.
:)

---

