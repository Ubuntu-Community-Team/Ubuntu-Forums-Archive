---
title: "Desktop file permissions screwed up..."
date: 2009-06-02
forum: General Help
---

### Post by steinaro on 2009-06-02
Help Please!!!!!
I am working on some php files for apache on my desktop so I created an apache alias to my desktop. Today I wrote some files at work so when I came home I was excited to plop them on my desktop and try them out in Firefox (I don't have access to a server at work). I called up localhost and got a 403 permission error. So I went to the internet and found a solution where I could change the permissions using the following:

sudo chown -R root:root /home/username/Desktop

sudo chmod -R 755 /
home/username/Desktop

sudo /etc/init.d/apache2 restart
Anyway it worked to load the page in Firefox but it apears I have messed up my permissions so that I can not simply work on my Desktop anymore with files i.e. to save anything I need permission.

How do I get my permissions back to normal. I have no idea how chown and chmod work.

---

### Post by DBrocks on 2009-06-02
Not quite sure what your question is, but from what I'm getting, I think it's that you cant save to your desktop. If that's the case, run:
 
```
 
sudo chown -R username:username /home/username/Desktop
sudo chmod -R 664 /home/username/Desktop

```
 
Basically what happened is that you made root the owner of all your files on the desktop. Thus, write permission to the desktop directory is denied. chown gives it back to you, and the chmod gives your user read/write permissions. Here's a writeup of chmod: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by steinaro on 2009-06-02
Thanks, that worked. I had to restart Ubuntu though. I tried just logging out and back in but that made the icons disappear on the desktop.

Cheers!

---

### Post by DBrocks on 2009-06-02
Glad I could help you. Thats what these forums are for. What you accidentaly did was make the desktop root property, which means you as a normal user would not have any read/write permissions. Also, I might suggest you read the link I sent you. Its a pretty good tutorial on chmod and its functions. Happy Ubuntu-ing!

---

