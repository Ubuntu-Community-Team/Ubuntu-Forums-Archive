---
title: "I want to install a package, but can only find a .bin file"
date: 2006-06-02
forum: Desktop Environments
---

### Post by irv on 2006-06-02
I tried to install Java runtime package from the package manager (j2re1.4 and j2sdk1.4), but it will not download the files, so I went to the website and downloaded them myself, but the only packages I could find for linux was j2re-1_4_2_12-linux-i586rpm.bin, and j2re-1_4_2_12-linux-i586.bin. If I rename the first to j2re-1_4_2_12-linux-i586.rpm and use sudo alien j2re-1_4_2_12-linux-i586.rpm it error and tells me it is not a rpm file.
My question is how do I install from a bin file?

---

### Post by Lux Perpetua on 2006-06-02
The download page has instructions. Take a look: [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

You should execute the file directly.

---

### Post by bjc on 2006-06-02
Have you looked at the Sun Java packages? You may prefer them to installing bin files. :-)

```

ben@dev:~$ sudo apt-cache search sun-java
sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-demo - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-plugin - The Java(TM) Plug-in, Java SE 5.0
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files

```

---

### Post by NewWithoutClue on 2006-06-02
Hmm,

file.bin indicates that this file is a binary file. Normally when you get a file in this format from a site, you execute it. To do this you need to open up a Terminal and change to the directory containing the file in question using the "cd" command. So if the file were in "/home/newwithoutclue/mydownloads", you would "cd /home/newwithoutclue/mydownloads". Once in the directory you need to try and execute your .bin file. To do this you just need to "sudo ./filename.bin" (we are ONLY using sudo to execute this file because we trust it(right?) and we know it's going to install something, and we also know that inorder to install most things we need to be root). If you get an error saying "Permission Denied" don't freak out and say Linux said "No" to root and run to blame Linus, instead make the file executable by executing the command "chmod +x file.bin". From this point on "./file.bin" will execute the file because it now has the execute permission set on it.

I'm VERY VERY sorry if I have totally lost you and you are still lost. However, I am sure there are TONS of guides/howtos/tutorials that can be found on Google.ca that will help you out. Try searching for "Linux file permissions" or "installing software on linux".

Regards,
Paul

---

### Post by irv on 2006-06-03
Thanks to all, I have JAVA installed. I do have another question, but I will make another thread because it deals with another subject.
Thanks again to all.

---

