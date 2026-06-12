---
title: "What next......?"
date: 2009-04-30
forum: General Help
---

### Post by andypearce on 2009-04-30
I have tried to get help a couple of times about my sound... sometimes normal sometimes half speed and sometimes one note at a time. I have had some good advice and help (but no cure) with 8.10 but now the problem is worse with the upgrade.....if the sound is slow so is the dvd and flash. My most recent plea for help got no response so what next... abandon ubuntu?, re-post my message? is there anywhere else I could go for help? I am new to this but really want to stay away from microsoft... I don't understand half of the language used in the other threads but have managed to get familiar with the basics of this system. Any suggestions would be appreciated.

---

### Post by 3Miro on 2009-04-30
Don't get discouraged if you cannot get an answer the first time. Not everyone knows how to fix every problem and everyone cannot follow all the threads and questions.

When you ask a question try to be as specific as possible. What exactly is your problem? What exactly is your hardware? What exactly is your system?

If we cannot help, you can turn to other places. If you purchase a Linux pre-installed computer from some companies, you may get support from them (System76 for example). You can purchase support from Canonical (however, that is somewhat on the expensive side).

---

### Post by andypearce on 2009-04-30
Thanks for the advice.... I am on a toshiba laptop that used to run XP.... I don't know how to describe the 'hardware' other than that... I will post again though if it does not sort itself out
Ta andy.

---

### Post by ajgreeny on 2009-04-30
For your hardware you could always attach the text file *lshw.txt* that will be made in your home folder from the command ```
sudo lshw > lshw.txt
```  That will give complete chapter and verse of everything in your machine and can be a very helpful way to see what is being dealt with.

---

### Post by 3Miro on 2009-04-30
> **ajgreeny said:**
> For your hardware you could always attach the text file *lshw.txt* that will be made in your home folder from the command ```
sudo lshw > lshw.txt
```  That will give complete chapter and verse of everything in your machine and can be a very helpful way to see what is being dealt with.

It may not work. You can try:
```

sudo ls
sudo lshw >lshw.txt

```

After the first sudo, you will have to give your password. The second one will create the file. You have to run the commands in the terminal (Applications -> Accessories -> Terminal). Copy and paste the two lines one by one.

Then open Places -> Home and you should be able to see the lshw.txt file there.

---

### Post by ajgreeny on 2009-04-30
> **3Miro said:**
> It may not work. You can try:
```

sudo ls
sudo lshw >lshw.txt

```After the first sudo, you will have to give your password. The second one will create the file. You have to run the commands in the terminal (Applications -> Accessories -> Terminal). Copy and paste the two lines one by one.

Then open Places -> Home and you should be able to see the lshw.txt file there.
No, you don't need the first of those two command first as far as I can see.  What do you think that adds to the second command, 3Miro?

---

### Post by 3Miro on 2009-04-30
> **ajgreeny said:**
> No, you don't need the first of those two command first as far as I can see.  What do you think that adds to the second command, 3Miro?

When you first open the Terminal, you do not have sudo privileges. When you run sudo lshw >lshw.txt you are being prompted for password, however, the "Enter Password" text goes to the text file and all you see is a blinking cursor on the screen. You can still enter the password, but you have to know that that's what is expected of you.

A generic sudo command will give proper prompt for the password and the terminal will assume sudo privileges for the time being, so the second command will execute normally.

---

### Post by ajgreeny on 2009-04-30
> **3Miro said:**
> When you first open the Terminal, you do not have sudo privileges. When you run sudo lshw >lshw.txt you are being prompted for password, however, the "Enter Password" text goes to the text file and all you see is a blinking cursor on the screen. You can still enter the password, but you have to know that that's what is expected of you.

A generic sudo command will give proper prompt for the password and the terminal will assume sudo privileges for the time being, so the second command will execute normally.
Sorry, now I'm completely lost!  ```
sudo lshw >lshw.txt
``` does exactly what I said it does without running ```
sudo ls
``` first.  Did you mean to run ```
sudo lshw
``` as the first command just to see the output appearing in terminal?  That could explain my confusion.

---

### Post by yoasif on 2009-04-30
while you may get some help on the forums, you may have found a bug in the system, so if the fixes that you are getting are not helping, you may want to report a bug.

you can also try going to #alsa on irc.freenode.net and seeing if they can help you.

they will ask you to run > wget [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) -O alsa.sh && bash alsa.shso do that and post the URL in any post you make on the forum, and also when you file a bug report. 

[file a bug report here]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug").

---

### Post by lisati on 2009-04-30
> **andypearce said:**
> Thanks for the advice.... I am on a toshiba laptop that used to run XP.... I don't know how to describe the 'hardware' other than that... I will post again though if it does not sort itself out
Ta andy.

What model Toshiba laptop are you using? There are a few of us around on the forums who use one sort or another, and there might be someone who uses one similar to yours.

---

### Post by andypearce on 2009-05-03
hi all.... I have just got the file into home as suggested. It tells me I am using a notebook, satellite pro L100, made by toshiba version PSLA4E-009009EN. I thought my problem might be something to do with the sound card during boot up (pressing the start button.... is that the right phrase)but cannot find a sound card on the list but assume as I get occasional sound that I have one! Any suggestions.
Thanks to all.
Andy.

---

### Post by andypearce on 2009-11-28
Hi all upgraded to 9.10 and it now works perfectly
Thanks
Andy

---

