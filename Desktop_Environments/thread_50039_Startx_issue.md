---
title: "Startx issue"
date: 2005-07-18
forum: Desktop Environments
---

### Post by dave9191 on 2005-07-18
Hey guys, 

Ive recently decided to do away with a graphic login since I just use fluxbox these days. So Ive set everything up so that when the computer boots it stops at the command line login, i log in there and type startx and presto. 

But I want to go one step beyond :) When I log in on the first console I want startx to load automatically and if I log into one of the other consoles not to run startx. So I added a few lines to my .bash_profile, a nice if statement that executes startx if I am loggin on the first console. 

But alas I run into a problem. When it runs startx from the .bash_profile it outputs a message saying I am not authersied to start the x server. But when it gives me the command line and I type startx there it works fine. I even got the bash_profile to echo $USER just to check if it was running as someone else, but its running as me.

What can I do ? 

Dave

---

### Post by evilghost on 2005-07-18
Perhaps:

```

#!/bin/sh
sudo -l {username} startx

```

---

### Post by dave9191 on 2005-07-18
Well I decided to try out combinations of what you suggested instead. sudo -l {username} cmd doesnt work as far as sudo syntax is concerned. So I tried sudo -u dave startx & instead. And I shoved that into a seprate shell script, executed by bash_profile, but it wouldnt work. And I tried to run that shell script from the command line and it wouldn't work. Untill I got rid of the & from the command it fails to run startx in a shell script. But the command works fine with the &  typed directly into the command line. Which I find strange. 

Anyway I just put startx without the & into my bash_profile and it works like a charm. Thanks for the input, it led me to the solution :)

Dave

---

