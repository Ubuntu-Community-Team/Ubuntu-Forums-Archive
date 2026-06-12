---
title: "Problem installing STATA"
date: 2008-10-30
forum: Education &amp; Science
---

### Post by nathanhutto on 2008-10-30
Hi all,

I'm running into a glitch installing STATA/SE 10 on Ubuntu. And I'm new to this, which makes it all the more complicated. I've gotten to the part where I need to run the license installer, requiring the command
[CENTER]./stinit[/CENTER]

When I type this, I get an error message saying "cannot execute binary file." Any thoughts on this?

Thanks much,
Nathan

---

### Post by chamb244 on 2008-10-31
I'm having the same issue.  Hopefully someone has some wisdom to share...

---

### Post by ciscosurfer on 2008-10-31
Does this help? [http://www.stata.com/support/faqs/unix/linux_install10.html](http://www.stata.com/support/faqs/unix/linux_install10.html)

---

### Post by chamb244 on 2008-11-02
thanks! doesn't help in my case, unfortunately. :(  I'm quite sure that I've got stata installed correctly, but in trying to run the initialization file (stinit), stata tells me "I don not find the file stata or xstata in the current directory.  Please change to the directory in which Stata is installed and type stinit again."  I've updated my PATH variable to include the directory.  (but that should matter anyway, right?, since I'm running ./stinit from the same directory where stata and xstata are already installed..)  i can't figure out why stinit is not seeing the rest of the installation. I've rebooted, etc etc.  Can't see what else i can adjust or experiment with.

---

### Post by ciscosurfer on 2008-11-02
Let's take the instructions step by step and see if we can get this puppy to work:

   To install Stata for Unix/Linux: 

Skip steps 1 through 4 and go straight here:```
sudo mkdir /tmp/statainstall
sudo cp -a /media/cdrom0/* /tmp/statainstall
sudo mkdir /usr/local/stata10
cd /usr/local/stata10
sudo /tmp/statainstall/install
# if that line doesn't work, run this:
sudo ./tmp/statainstall/install
```Step 5: Once the installer has completed, you must initialize the license by        typing ./stinit
I assume this file is sitting under the /usr/local/stata10 directory now.  What are its permissions?  Can you give me a long listing of this file as well as it's parent directory and /media/cdrom0```
ls -lh /media/cdrom0
ls -lh /tmp/statainstall
ls -lh /usr/local/stata10

```Post the output and we'll go from there.

---

### Post by nathanhutto on 2008-11-03
Thanks for your help. When I type ./stinit, I get an error message saying "cannot execute binary file." I'm not sure how to get an output to post here. Can you advise?

---

### Post by ciscosurfer on 2008-11-03
The best way for me to assist you at this point is for you to follow the instructions I gave you in my last post.  Without seeing the permissions of the files you've installed, it's hard to say what to do next.  It does sound like a permissions issue though.

---

### Post by chrisby on 2009-02-08
I think "sudo ./stinit"  should do it.

---

### Post by gatorbrit on 2009-02-09
I don't have the instructions on me, but I recently did this and I followed the instructions in the stata for linux manual to the letter and it worked great.

---

### Post by ecoxmit on 2009-10-13
be sure you are selecting the right Intel processor and 64/32bit option when installing.

---

