---
title: "[SOLVED] Dell Mini 9. error message. can't get skype to install."
date: 2008-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2008-11-12
I downloaded the the skype version of linux on skype.com.

I clicked on the Ubuntu 7.04+ version. I downloaded the entire file, which is 14.8 Megabytes.

The file name is: skype-debian_2.0.0.72-1_i386.deb

I right clicked and clicked on GDebi package installer.

it loaded.

it says:

Package: Skype

Status: Error: Wrong Architecture 'i386'

can't get it to install. I am thinking either dell messed up my ubuntu install. or there custom ubuntu version has bugs that aren't fixed yet.

i was thinking of formatting my ubuntu and reinstalling it. But I think that is a last resort thing to do.

does anyone else that has a dell mini 9 pre-installed with ubuntu have this problem?

---

### Post by sirebral on 2008-11-12
You should be able to just double click it and it will install.

I think Skype for Linux is bumkiss and not very well done.  But I use it.

---

### Post by shiningkenmonster on 2008-11-12
I did double click on it too. its the same error message. skype is still not installed.

has anyone got their skype to install with their dell mini 9?

---

### Post by ArKay on 2008-11-12
The problem is that the architecture for the package is expecting a i386 compile of Ubuntu where the installed version on the mini is specially compiled to used the atom lipa architecture.

There are a couple of methods to fix that - one is repackaging it using a few different methods, another is a command to force it to be installed and the third is to reinstall a copy of Ubuntu which is set up to deal with that.

Search on 'install skype' and you should be able to find the different methods.

Here is method 1 :
I am reposting here, with links:

1. Download the Ubuntu package from Skype
2. open terminal (menu Accessories)
3. move into the folder you downloaded the package
4. Type:

Code:

sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb


And here is another :
Quote:
Originally Posted by feranick View Post
Really the i386 deb is a non issue. You can easily repackage any deb outside the repos into an lpia one. And really there aren't many. The reason you want lpia packages instead of forcing the i386, is that while the former will show up as an installed package on Synaptics, the later won't, so good luck uninstalling it. For example here's the directions to convert the stock i386 package for Skype into an lpia package:

1. Download the Ubuntu version of Skype
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the debian-binary file
6. Decompress control.tar.gz. There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN, "control". Change the line "Architecture: i386" into "Architecture: lpia"
9. Open the other archive data.tar.gz. There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files control.tar.gz and data.tar.gz
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!


Besides, I made a bunch of backports from standard Ubuntu repositories, all working great in my mini once packaged as lpia.
/quote

Hope those help.

---

### Post by yakker.yak on 2008-11-12
You should be able to update to a newer version of the package installer (Gdebi) that will install i386 DEBs into your LPIA Dell Ubuntu. The two architectures are different but compatible.

So, try to upgrade Gdebi first, then try the default i386 Skype DEB again.

Gdebi update:

[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb)

---

### Post by shiningkenmonster on 2008-11-13
> **yakker.yak said:**
> You should be able to update to a newer version of the package installer (Gdebi) that will install i386 DEBs into your LPIA Dell Ubuntu. The two architectures are different but compatible.

So, try to upgrade Gdebi first, then try the default i386 Skype DEB again.

Gdebi update:

[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb)


crap, i think i accidentally deleted the Gdebi

i downloaded that link. and it was installing. than it asked me to type something in the terminal.

something like:

sudo apt install -a

sorry, i only remember some of it. it was something like that along the line.

It was installing. but than it asked me to delete Gdebi and would you like to continue. I typed in Y for Yes, and it deleted it. (i thought it was asking me to delete the old Gdebi software.)

anyways, I tried to install the Skype, but it opens with the Archive Manager.

when i right click on the skype file, it doesn't show the  "GDebi package installer" - like it used to before

only shows Archive Manager.

I tried to play around with it on my own. but i'm screwed.

is there a way to have back GDebi Packager installer again?

i think i should of listen to ArKay and take the long way instead.

---

### Post by yvinogradov on 2008-11-13
Alternative method of repackaging Skype (or any other) package originally packaged for i386 architecture into a package for lpia architecture

USE AT YOUR OWN RISK

1. download Skype package, preferably to a not very crowded folder
2. execute 'dpkg -x <skype_package_name>   skype'
3. execute 'dpkg -e <skype_package_name>   skype/DEBIAN'
4. execute 'cd skype'
5. open file DEBIAN/control in the text editor of your choice, find the line that says 'Architecture: i386', replace i386 with lpia, save and close the file
6. execute 'dpkg -b . ..; cd ..; ls *.deb' and notice that there is a new package present with lpia in it's name instead of i386
7. execute 'sudo dpkg -i <new_skype_package_name>'

optional - after making sure that Skype works clean up by executing 'rm -r skype; rm *skype*.deb'

note: when typing <skype_package_name> and <new_skype_package_name> DO include file extrensions '.deb'

---

### Post by JoeinDallas on 2008-11-13
I think I ran into this same issue when trying to install skype and also managed to mess up gdebi.

Here is the whole thread  [http://www.mydellmini.com/forum/*-deb-installing-t433.html](http://www.mydellmini.com/forum/*-deb-installing-t433.html)  , but basically I just had to go to a terminal and install from there:  gdebi skypeblahblah.deb and it worked!  Skype is running just fine.  I don't know if I deleted the "ability to graphically run gdebi from the gui" or just broke an association, but that's for another day.

Joe

---

