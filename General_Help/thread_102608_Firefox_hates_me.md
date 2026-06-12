---
title: "Firefox hates me"
date: 2005-12-12
forum: General Help
---

### Post by Rosette on 2005-12-12
I'm having a bitch of a time installing Firefox 1.5. From the website it tells me to unpack the tarball into the directory I want to install it to. So I did this (home, mozilla, firefox) yet I still get 1.0.7 coming up when I click the shortcut. Also, Firefox keeps deleting my bookmarks etc. Anyone have any suggestions? I must be doing something wrong...

---

### Post by Qrk on 2005-12-12
Can you run it from the folder where you installed it? Its the .sh file named "firefox."

---

### Post by potrick on 2005-12-12
Hey, try this script from arnieboy. It's a bit easier than the tar ball. Worked beautifully for me. 


[http://ubuntuforums.org/showthread.php?t=99004&highlight=firefox+1.5](http://ubuntuforums.org/showthread.php?t=99004&highlight=firefox+1.5)

Enjoy!

---

### Post by Suzan on 2005-12-12
What's difficult to install firefox?

If you have the firefox unpack in a directory, e.g. /opt you have to modify your symbolic link, if you want to start the new one with the command "firefox":

```

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

You can read a very good description in the wiki:

[Installing Firefox from mozilla.org](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

---

### Post by Rosette on 2005-12-12
I tried everything listed [here]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29") but it didn't work... now the only way I can even get on Firefox is by going through the bug report :P Ironic. So nothing works. I'm getting fed up now... I do everything the guides tell me to do but still nothing goes right.

---

### Post by Suzan on 2005-12-12
You unpack Firefox in what directory?

What happens if you start FF with the terminal? 

If you unpacked FF in /opt type in the terminal

```
/opt/firefox/firefox
```

What happens then? Does FF start or do you get an error?

---

### Post by Curlydave on 2005-12-12
It sounds to me that you're unpacking Firefox, then running the old one. Unpacking the tar file from the Mozilla website just creates a directory with the new FF. It does NOT get rid of the old one. To run FF 1.5 this way, you need to create shortcuts to the "firefox" sh script in the unpacked directory.
 
I wrote a HOW-TO on setting up these shortcuts in the customizations forum: [http://www.ubuntuforums.org/showthread.php?t=98530](http://www.ubuntuforums.org/showthread.php?t=98530)

---

