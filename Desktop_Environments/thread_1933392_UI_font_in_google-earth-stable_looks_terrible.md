---
title: "UI font in google-earth-stable looks terrible"
date: 2012-02-29
forum: Desktop Environments
---

### Post by emanuel.landeholm on 2012-02-29
Ubuntu 11.10 (Oneiric). Unity 3d. google-earth-stable installed from: [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

What I have tried so far (from googling):

+ I have tried installing ttf-mscorefonts-installer and reinstalling google-earth-stable
+ qtconfig-qt4 font size

I had this working in Natty. Different computer but still...

I can't believe google earth doesn't have better support for the number one Linux distribution! Blows my mind...

Window shot:

[http://twitpic.com/8q52mq](http://twitpic.com/8q52mq)

cheers,
Emanuel

---

### Post by howefield on 2012-02-29
Have a browse here...

[http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/](http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/)

---

### Post by emanuel.landeholm on 2012-02-29
> **howefield said:**
> Have a browse here...

[http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/](http://www.omgubuntu.co.uk/2012/01/how-to-make-google-earth-look-native-in-ubuntu/)

That looks rather promising... However, I got the following error when starting google-earth after following the instructions given in the blog.

```
./googleearth-bin: symbol lookup error: /usr/lib32/libQtWebKit.so.4: undefined symbol: _ZN28QNetworkConfigurationManagerC1EP7QObject
```

So I guess I need to apt-get install qtwebkit something?

cheers,
Emanuel

---

### Post by howefield on 2012-02-29
Hmm, worked straight off for me without having to follow the trouble shooting stage  at the foot of the article.

Shouldn't hurt to give it a go.

> Troubleshooting

Nothing working afterwards? You probably need a few extra packages. Open a terminal and enter the following: -

sudo apt-get install libcurl4-openssl-dev libqtwebkit4

---

### Post by Pengwyn44 on 2012-05-05
Have you checked that you have the correct graphics driver?
When I upgraded to 12.04, Google Earth would not run, I just had an error message.
The reason is that when downloading a new Ubuntu release the proprietry drivers are switched off. Go to System Settings, click on Hardware - Additional Drivers and Activate.
G E now works normally.

---

