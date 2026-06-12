---
title: "How to encrypt my sensitive data ( USB or a few folders in Home directory ) ?"
date: 2009-05-20
forum: General Help
---

### Post by ActiveFrost on 2009-05-20
For geeks - are there any encryption tools so I could encrypt "sensitive" files/folders ?
I have a few VERY sensitive files ( passport scan, etc. ) on my USB + a few similar files in my Home directory, so .. I would like to protect them from being used by someone else ( I don't care, brother, sister or a hacker - I want them to be protected ).

Any ideas/suggestions/tutorials/articles ? :)

---

### Post by Soul-Sing on 2009-05-20
Truecrypt.
: [http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

---

### Post by binbash on 2009-05-20
+1 truecrypt

---

### Post by ActiveFrost on 2009-05-20
> **leoquant said:**
> Truecrypt.
: [http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

Thank you. Will take a look at it :)

---

### Post by t0p on 2009-05-20
I use **cfs**.  But it's a command-line utility, which isn't to everyone's taste.

As I remember, with Intrepid it is possible to use **ecryptfs** to create an encrypted directory in your /home directory.  But that might need to be enabled at the time of installation. Sorry, can't remember for sure. :(

By far the most popular solution is [Truecrypt]("http://www.truecrypt.org").  If you follow that link to the project's website, you'll find there are packages available for Linux, including the .debs Ubuntu needs. But having said that, I believe it's in the repos now.  So

```
sudo apt-get install truecrypt
```

should get you the latest version.  Truecrypt can create encrypted directories for you, and also supports the use of removeable media (eg CDs... maybe USB sticks, I dunno...) which can be taken away and used with other computers including machines that run Windows.

---

### Post by XCan on 2009-05-21
I would say truecrypt as well. It's very easy to use, although I think only some front ends are available in the standard repository setup. I installed it simply by downloading the .deb file from [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) which comes with a gui. 

You can create file containers using truecrypt which may suit your purposes very well.

---

### Post by Soul-Sing on 2009-05-22
> **XCan said:**
> I would say truecrypt as well. It's very easy to use, although I think only some front ends are available in the standard repository setup. I installed it simply by downloading the .deb file from [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) which comes with a gui. 

You can create file containers using truecrypt which may suit your purposes very well.

The new truecrypt does't need a frontend or gui, it (truecrypt) comes with a gui and a wizard to set up containers and volumes. So easycrypt as a gui for truecrypt (which in the repos.) isn't needed anymore. Truecrypt itself isn't in the repos. of ubuntu.
The earlier versions of truecrypt were terminal based....

---

### Post by XCan on 2009-05-22
> **leoquant said:**
> The new truecrypt does't need a frontend or gui, it (truecrypt) comes with a gui and a wizard to set up containers and volumes. So easycrypt as a gui for truecrypt (which in the repos.) isn't needed anymore. Truecrypt itself isn't in the repos. of ubuntu.
The earlier versions of truecrypt were terminal based....

Yah, that's what I said in my post. :p

---

### Post by dozch on 2009-06-13
My reply is a bit late but I found these pages in the community docs useful:

[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage]("https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage")

[https://help.ubuntu.com/community/EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

---

### Post by Soul-Sing on 2009-06-13
> **dozch said:**
> My reply is a bit late but I found these pages in the community docs useful:

[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage]("https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage")

[https://help.ubuntu.com/community/EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

Indeed very useful, espec. the last one.

---

### Post by Subban on 2009-06-13
I was looking for something to just similarly provide some encryption on a limited number of documents... wife + digital camera=encryption needed

Cryptkeeper seems simple and sufficient while truecrypt seemed larger than necessary for such a moderate use, but not having used it that was my impression rather than based on experience.

---

### Post by Soul-Sing on 2009-06-13
```
Basically Cryptkeeper is a Linux system tray applet that manages EncFS encrypted folders. In this simple etc...
```

Do you use this? I mean the system tray aplet?

---

### Post by Soul-Sing on 2009-06-13
Hmm cryptkeeper home website has a server error.
And getdeb hasn't the .deb anymore....

---

### Post by Subban on 2009-06-13
> **leoquant said:**
> ```
Basically Cryptkeeper is a Linux system tray applet that manages EncFS encrypted folders. In this simple etc...
```

Do you use this? I mean the system tray aplet?

Yes it is a tray applet and I understand it is something to do with the EncFS, any more than that I haven't researched.

---

### Post by Subban on 2009-06-13
> **leoquant said:**
> Hmm cryptkeeper home website has a server error.
And getdeb hasn't the .deb anymore....

I installed it via synaptic as I recall.

---

### Post by HermanAB on 2009-06-13
Here you go:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by ActiveFrost on 2009-06-13
Thanks to everyone who've helped so far - I've found the easiest ( &best ) way to encrypt my data .. TrueCrypt :)

---

