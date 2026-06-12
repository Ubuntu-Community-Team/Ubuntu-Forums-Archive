---
title: "Getting Webcam to work"
date: 2009-02-28
forum: General Help
---

### Post by phr33k-dc on 2009-02-28
How do i get my webcam working? sony vaio AW series?

---

### Post by phr33k-dc on 2009-02-28
Do i have to download any drivers or anything?

---

### Post by substanceD on 2009-02-28
Have you tried running a program that uses your webcam to see if it does anything? Maybe install XawTV and see if it gets input from it; do

```
sudo apt-get install xawtv
xawtv
```

My laptop's webcam didn't require any special drivers to make it work--I have an Asus M-51 series notebook.

---

### Post by phr33k-dc on 2009-02-28
ye tryed using a program that uses a webcamand got- '/dev/video0 not found'

---

### Post by substanceD on 2009-02-28
Have you tried using EasyCam? It can apparently help with installing webcam drivers in Ubuntu. Here's a link: [https://help.ubuntu.com/community/EasyCam]("https://help.ubuntu.com/community/EasyCam").

---

### Post by aikiwolfie on 2009-02-28
Have you tried installing Cheese? Just use the following command in a terminal window.

```
sudo apt-get install cheese
```

When you run the command you'll be promted for your password. Enter it and everything should just work. The install takes about two minutes and you're ready to roll.

---

