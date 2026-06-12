---
title: "Super Meat Boy"
date: 2012-06-10
forum: Gaming &amp; Leisure
---

### Post by Welly Wu on 2012-06-10
I purchased the Humble Indie Bundle V for $8.00 USD using my PayPal account and they recently added three additional PC games for Ubuntu including Super Meat Boy. There is a supermeatboy-linux-06072012-bin file in my Downloads folder in my /home partition. I tried to install it using sudo sh supermeatboy-linux-06072012-bin and I used the Ubuntu Software Center. Both failed to install properly. How do I install Super Meat Boy?

---

### Post by Welly Wu on 2012-06-10
Here is my terminal output:

wellywu@N61JV-X2:~$ cd Downloads
wellywu@N61JV-X2:~/Downloads$ ls
android-sdk-linux  supermeatboy-linux-06072012-bin
wellywu@N61JV-X2:~/Downloads$ sudo chmod +x supermeatboy-linux-06072012-bin 
[sudo] password for wellywu: 
wellywu@N61JV-X2:~/Downloads$ ls
android-sdk-linux  supermeatboy-linux-06072012-bin
wellywu@N61JV-X2:~/Downloads$ sudo sh supermeatboy-linux-06072012-bin 
supermeatboy-linux-06072012-bin: 1: supermeatboy-linux-06072012-bin: Syntax error: "(" unexpected
wellywu@N61JV-X2:~/Downloads$

---

### Post by sffvba[e0rt on 2012-06-10
*Thread moved to **Gaming & Leisure**.*


404

---

### Post by stigb on 2012-06-10
You could try installing it from the Ubuntu Software Center. From the page where one downloads the games, there's a link to download from the USC. It worked for me!

---

### Post by Welly Wu on 2012-06-10
I tried that. The Ubuntu Software Center wants me to pay for Super Meat Boy when Humble Indie Bundle V recently added it and two other PC games for free. I do not want to pay for Super Meat Boy again.

Let me check my key to see what I can do.

---

### Post by Welly Wu on 2012-06-10
It works. I clicked on the url within the e-mail message that was sent to me by Humble Indie Bundle and I clicked Download for Ubuntu for Super Meat Boy. I put in my Ubuntu credentials and I put in my root password. It is installing Super Meat Boy now. This is solved.

---

### Post by Libervurto on 2012-10-02
Hello, I have SMB installed but it fails to launch. Any ideas?

---

### Post by thatguruguy on 2012-10-02
> **Libervurto said:**
> Hello, I have SMB installed but it fails to launch. Any ideas?

You might want to run it from a terminal and let us know any error messages that are generated.

---

### Post by AbhishekGupta0693 on 2012-11-03
hey its an executale file ,have you tried intalling it by using simply double clicking the file

---

### Post by pqwoerituytrueiwoq on 2012-11-03
i think that was available in .deb format, i know i had it installed in 10.04
when you chmod +x something you don't need to run it in sh, you can let the file determin how to run it (sh/bash/dash/php)
so run it like this (assuming the bin is a installer)
sudo supermeatboy-linux-06072012-bin

---

### Post by destroyerzx1 on 2013-05-28
> **Welly Wu said:**
> Here is my terminal output:

wellywu@N61JV-X2:~$ cd Downloads
wellywu@N61JV-X2:~/Downloads$ lssupermeatboy-linux-06072012-bin
android-sdk-linux  supermeatboy-linux-06072012-bin
wellywu@N61JV-X2:~/Downloads$ sudo chmod +x supermeatboy-linux-06072012-bin 
[sudo] password for wellywu: 
wellywu@N61JV-X2:~/Downloads$ ls
android-sdk-linux  supermeatboy-linux-06072012-bin
wellywu@N61JV-X2:~/Downloads$ sudo sh supermeatboy-linux-06072012-bin 
supermeatboy-linux-06072012-bin: 1: supermeatboy-linux-06072012-bin: Syntax error: "(" unexpected
wellywu@N61JV-X2:~/Downloads$

better late then never but the problem is the file name is supermeatboy-linux-06072012-bin <-- see the dash before it says bin that needs to be a period ( . ) so supermeatboy-linux-06072012.bin then you can run 

chmod +x supermeatboy-linux-06072012.bin
sudo ./supermeatboy-linux-06072012.bin

and it should execute

---

