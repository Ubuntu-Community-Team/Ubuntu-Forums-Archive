---
title: "Running consecutive sudo commands"
date: 2009-02-13
forum: General Help
---

### Post by xero_alpha on 2009-02-13
Hi all,

I've been using Intrepid Ibex for a little while now and just getting used to using to tinkering with Terminal commands.

As newbies do, I have been experimenting with creating .mkv files through Terminal using sudo codes. 

The problem is it takes a while to convert video, then audio, then subtitles etc.. all of which I would have to sit there and type codes for each one after the other.

I would like to know if there is some way of automatically running a string of codes that follow each other once the other command is done. Eg. when the video finishes, the audio starts.

If you guys have any ideas it would be much appreciated. Cheers

---

### Post by solwic on 2009-02-13
> **xero_alpha said:**
> Hi all,

I've been using Intrepid Ibex for a little while now and just getting used to using to tinkering with Terminal commands.

As newbies do, I have been experimenting with creating .mkv files through Terminal using sudo codes. 

The problem is it takes a while to convert video, then audio, then subtitles etc.. all of which I would have to sit there and type codes for each one after the other.

I would like to know if there is some way of automatically running a string of codes that follow each other once the other command is done. Eg. when the video finishes, the audio starts.

If you guys have any ideas it would be much appreciated. Cheers

I think && works.  Like: ```
sudo command 1 && sudo command 2 && sudo command 3
```

And so on. 

Don't hold me to that, but I *think* that's how it works.

---

### Post by jerome1232 on 2009-02-13
Or better so that it doesn't require a password each time.

sudo -i give you a root shell, exit get's back out of the root shell.

```
sudo -i && command 1 && command 2 && command 3 && exit
```

On another note I can't see why you would need root privileges to just transcode videos... unless your saving these video's to a location your normal user doesn't have permission to access.

---

### Post by sujoy on 2009-02-13
and if you need to run the commands frequently, add them to a file like this

#!/bin/bash
command 1
command 2
...
exit

chmod +x filename

then you can run it directly

---

### Post by solwic on 2009-02-13
> **jerome1232 said:**
> Or better so that it doesn't require a password each time.

sudo -i give you a root shell, exit get's back out of the root shell.

```
sudo -i && command 1 && command 2 && command 3 && exit
```


I didn't know that.  Huh. Learn something new every day.  :)

---

### Post by xero_alpha on 2009-02-13
Thanks guys, sounds good, I'll give it a shot.

---

### Post by bodhi.zazen on 2009-02-13
> **sujoy said:**
> and if you need to run the commands frequently, add them to a file like this

#!/bin/bash
command 1
command 2
...
exit

chmod +x filename

then you can run it directly

... with sudo 

sudo /path/to/script

All scripts you run as root (via sudo) should be owned by root and not writable by any non-root user ;)

---

### Post by xero_alpha on 2009-02-13
Another thing, 

On the odd occasion it may ask me for permission to execute a command. (Y/N)

More often than not the answer would be Y. Do you think inputting "&&" between commands would interfere. If so, how would I get around that?

---

### Post by glotz on 2009-02-13
Try reading the manual page for the tool itself, there probably is a command line switch for that.

---

### Post by bodhi.zazen on 2009-02-13
> **xero_alpha said:**
> Another thing, 

On the odd occasion it may ask me for permission to execute a command. (Y/N)

More often than not the answer would be Y. Do you think inputting "&&" between commands would interfere. If so, how would I get around that?

By writing a bash script and executing the script rather then using && on the command line.

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by xero_alpha on 2009-02-13
Thanks. I'll give that a go too.

---

### Post by bodhi.zazen on 2009-02-13
I think you will find writing a bash script is fairly easy and very powerful, it will make your life on the command line much easier.

---

### Post by Joeb454 on 2009-02-13
Just to (hopefully) clear something up.

&& is a logical and operator. In this context - It will run the command, and if that succeeds, then it will go and do the next command etc.

If the first command fails, it will not run anything else. If the 2nd command fails, it stops there, etc.

I hope that clears a couple of things up :)

---

