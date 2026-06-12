---
title: "files on desktop"
date: 2009-05-11
forum: General Help
---

### Post by mikrodoctor on 2009-05-11
I am trying to run metapoit. I have downloaded, installed and I am now trying to run program. When I am in terminal I type ./msfconsole, I get  No such file or directory.The directory is there. If I change to the dir on my desktop I get same message. How can I get to the dir on my desktop in terminal?

Thank for the help:P

---

### Post by prem1er on 2009-05-11
If the file you want to run is on your desktop, open up the terminal and run.


```
cd /home/user/Desktop/filename
```

That will bring you to the correct location of the file, from there you should be able to run your program.

---

### Post by mikrodoctor on 2009-05-11
no still getting  No such file or directory

---

### Post by prem1er on 2009-05-11
Copy and paste the exact commands you run in your terminal.  I am either not understanding you, or you are leaving something out.

---

### Post by mikrodoctor on 2009-05-11
the directory on my desktop is framework-3.2 inside the directory is the file msfconsole that is the file I am trying to run.

the directory is there using file browser I can get in to the dir and see the file msfconsole.

I used the command you said to use 
cd /home/user/Desktop/framework-3.2/msfconsole

---

### Post by prem1er on 2009-05-11
> **mikrodoctor said:**
> the directory on my desktop is framework-3.2 inside the directory is the file msfconsole that is the file I am trying to run.

the directory is there using file browser I can get in to the dir and see the file msfconsole.

I used the command you said to use 
cd /home/user/Desktop/framework-3.2/msfconsole

Two things. 

1. You are replacing 'user' with your actual user name correct?

2. The 'CD' command only changes your current directory. So you will have to.

```
cd /home/user/Desktop/framework-3.2
```

....don't forget to replace 'user'.  And then....

```
./msfconsole
```

---

### Post by mikrodoctor on 2009-05-11
sorry I did not use my name instead of user. When I do type cd /home/roger/Desktop/framework/msfconsole  I still get No such file or directory

---

### Post by prem1er on 2009-05-11
You didn't read what I said.  There are two commands you have to type.  First 'cd' and then run your program. Read my previous post better.

---

### Post by mikrodoctor on 2009-05-11
Sorry about that I'm new to using command mode. Ok I am now in the dir framework-3.2
I type msfconsole
now I am getting command not found
 if I type  ls the file is there

---

### Post by mikrodoctor on 2009-05-11
looking at the file in file browser and right click and look at properties the file is a ruby script.

---

### Post by Cheesemill on 2009-05-11
You need to type ```
./msfconsole
```
whilst in the directory.

---

### Post by prem1er on 2009-05-11
After you are in the directory with the script, type.

```
./msfconsole
```

---

### Post by mikrodoctor on 2009-05-11
thankyou so much prem1er and Cheesemill that indeed worked. One last question just so I understand. If I'm in the proper dir what does ./ do? Does that not take you out of the dir your in and put you in root?

---

### Post by kanikilu on 2009-05-11
No, that doesn't take you out of your current directory. For the long-winded explanation, check out this page:

[http://www.linfo.org/dot_slash.html](http://www.linfo.org/dot_slash.html)

---

### Post by gradysghost on 2009-05-11
For the short explanation...

In the Linux file system, a single dot where you would normally type a folder's name means "this folder".  Two dots means "this folder's parent folder" or "up one level".

So when you type ./filename, you're giving it the command "In this folder, execute filename."  The file needs to be executable (more on that if you need, but the topic is very well defined elsewhere).

May I suggest [this book]("http://www.ubuntupocketguide.com/download_main.html")?  It's free for download, and very well-written.

---

### Post by mikrodoctor on 2009-05-11
thank you for your explanations that has helped a lot. There is a lot to learn being new to Linux but look forward to the challenge.:P

---

### Post by gradysghost on 2009-05-11
Glad to see you're willing to stick with it.  I think you'll like it when you know it.

---

