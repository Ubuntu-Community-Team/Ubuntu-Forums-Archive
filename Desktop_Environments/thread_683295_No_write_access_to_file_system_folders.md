---
title: "No write access to file system folders"
date: 2008-01-30
forum: Desktop Environments
---

### Post by jmichaels3 on 2008-01-30
Ok, I just installed Ubuntu Ultimate 1.4 and I really love it, but I can't seem to have write access to the file system folders.  If I want to copy a file I can open a terminal and do the following- sudo cp <file to copy> <place to copy too> or I can do - gksu nautilus and copy my files that way.

Here's my real problem.  I'm in college learning java programming. The entire java development kit is located in /usr/bin which I have no write access to.  So, I write my code in text editor and save it to my home folder.  Then I copy the file using the steps mentioned above to the folder where my java stuff is.  The problem is when I attempt to compile the program I get a permissions error again.  Very frustrating.  Is there a way to have write access all the time or do I need to try a different distro.  Thanks for your help.

---

### Post by Ptero-4 on 2008-01-30
you can use sudo -s in the terminal. But be aware that this opens a root shell, hence you need to remember to close it when you're done compiling your assigments.

---

### Post by jmichaels3 on 2008-01-30
Thank you for your guidance.  Your suggestion worked great.  I'm still kind of new to Linux.  I started playing with different distros a few months ago and I'm addicted to it now.  There's only one way to learn and that's to dive right in.  Thanks again for your help.

---

### Post by JBently on 2008-06-09
> **Ptero-4 said:**
> you can use sudo -s in the terminal. But be aware that this opens a root shell, hence you need to remember to close it when you're done compiling your assigments.

hi, im having the same problem - not being able to save files into folders in my File System directory.  Im trying the php tutorials out of a book and they want me to save them to my root directory but the only place I could think of that being is under File System -> Root  but i have no access to it.

Ive been asking on multiple forums but no ones gotten back to me yet.  I understand how to use terminal so can try the sudo -s suggestion but you say i'd need to make sure i close it when im done.  How do i close it then?

Also, do you think im correct in assuming the php files im writing need to go into File System -> Root ?  Or do they go into File System -> Usr -> Bin like the other person mentioned?  They are basic files that im then supposed to test by typing [http://localhost/phpinfo.php](http://localhost/phpinfo.php)   

Help is greatly appreciated!!
JB

---

