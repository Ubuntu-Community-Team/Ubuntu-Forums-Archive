---
title: "Synaptic Package Manager"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Thadd.Isolas on 2006-02-12
Hello,

I am new to linux and have installed this as a project to try and get myself used to linux and learn another operating system other than windows.  

I wish to use the synaptic package manager to install packages.  But I can't access the repositries.  I have enabled the Ubuntu 5.10 "Breezy Badger" (Binary) repositry with only "Officially supported" and "Restricted copyright" checkmarked.  I once I hit ok to accept the changes it tries to reload the package list but comes up with two windows with these error messages in them.

This is the first error message

> [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)

This is the second error message that pops up
> 
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

I don't beleive it would be the schools proxy.  I have already logged in before this and anything that normally requires that be logged in works.  So I don't beleive that this is what is causing the errors, although I am new thought it worth mentioning because I could very well be wrong ;).  Not sure what else could have caused it.  My connection works fine as far as I know, I am submitting this from the computer with the respositry problem after all.  

Hope this all made sense if I don't make sense don't be afraid to ask for a more specific diagnosis or something.  Thanks for your help!

Thadd

---

### Post by Madpilot on 2006-02-12
The various country archives (us.archvie, ca.archive, etc) have been having trouble lately. The best thing to do seems to be to just use the basic central Ubuntu repos.

Go through your sources.list an remove all the "us." from the beginnings of the line; hit Reload in Synaptic, and see if that fixes your error messages.

---

### Post by Thadd.Isolas on 2006-02-12
Nope, removed all the "us." from the source.list file and still end up with these after I hit reload.

> [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)

> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


Thanks for getting back to me so soon.

Thadd

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=Thadd.Isolas]Nope, removed all the "us." from the source.list file and still end up with these after I hit reload.




Thanks for getting back to me so soon.

Thadd[/QUOTE]
If you just copy the URL part and paste it in your browser, can you browse to any of the files successfully?

---

### Post by Thadd.Isolas on 2006-02-12
Well I can access [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) and browse around but what's written in the source.list file is

 # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

and I can't use the full thing with spaces.  But yeah, I can browse around in [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

---

