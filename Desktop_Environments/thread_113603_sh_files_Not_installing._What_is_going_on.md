---
title: "sh files Not installing. What is going on?"
date: 2006-01-06
forum: Desktop Environments
---

### Post by shade11 on 2006-01-06
I have encountered a few files that arent in the synaptic package list. So I am unfamilar on how to install them. I know how to install a shell file but they wont work. There was one that I downloaded that just had one sh file. And it was confusing. I cd to the location then I type in ./configure (I even tried to type in ./(the sh file name)) then I type in make then type in make install but it doesnt work. Does anyone have any ideas?

EDIT: I have also tried
cd directory-name-where-the-file-is
sudo ./nameofshellfile.sh
but is says command not found.

---

### Post by endy on 2006-01-06
Please post the exact package you are trying to install. I may not be able to help but the more information we get the better chance you have of getting a solution :D

---

### Post by shade11 on 2006-01-06
crossover office pro and glTron (I hate armagetroon)

---

### Post by endy on 2006-01-06
Heh, well at least I was right about one thing today, I can't really help further because I don't have that.

Sorry.

I would have thought you could call on Codeweavers for technical support...

---

### Post by shade11 on 2006-01-06
Ok I will try that. But what was the reason you posted. Becasue I saw no reason to.

---

### Post by zappa86 on 2006-01-06
I'm not sure if i understand you. are you trying to run a .sh file. I know my nvidia installer is a sh file. What I have to do is set the execute bit becasue its not there by default. cd to the file's directory and do:
```
chmod +x <your file>
```
then you should be able to do a ./<your file> If it installs something it may require root access. therefore you should do a sudo or a su so it can write where it needs to go.

---

### Post by Ubluntu on 2006-01-06
did you try typing: sh ./configure ?? I noticed some stuff won't run without useing sh.. Some programs also need you to run the sh script while your in its parent directory or whatever directory you might be installing it.

---

### Post by shade11 on 2006-01-09
Didn't work. I am getting tired of this. I can never install anything from source. But on the Positive side I did manage to install Crossover office.

---

### Post by neoflight on 2006-01-16
is it just ./filename rather than ./filename.sh?
correct me if i am wrong...???

try sudo sh filename.sh????

---

### Post by shade11 on 2006-01-16
[QUOTE=neoflight]is it just ./filename rather than ./filename.sh?
correct me if i am wrong...???

try sudo sh filename.sh????[/QUOTE]

I have done this. But neither work.

---

### Post by RAOF on 2006-01-16
Ok, it's obvious that we need more information to help you.  Since you got Crossover working, let's do glTron:

1) What was the file that you downloaded? (I guess it would be something.tar.gz, or similar)
2) You extracted this archive somewhere, yes?  What are the files in that extracted directory?  Could you post the output of "ls -l" in that directory?
3) Chances are, there is a file called README or INSTALL or similar.  Is there anything in them?  What instructions do they give?

---

### Post by shade11 on 2006-01-16
Forger about glTron I have already figured out how to run it. since it was a single shell file i did the same thing with Crossover Office. Also glTron was in Synaptic so I got it there. But I got rid of it becuase gltron is slow and unstable. 

Right not I want to be able to install a program from source.

I cant do the:
./configure
make
make install
Thing
at all.
I wanted to install bmpX and it wasnt in Synaptic.

---

### Post by RAOF on 2006-01-16
[QUOTE=shade11]Forger about glTron I have already figured out how to run it. since it was a single shell file i did the same thing with Crossover Office. Also glTron was in Synaptic so I got it there. But I got rid of it becuase gltron is slow and unstable. 

Right not I want to be able to install a program from source.

I cant do the:
./configure
make
make install
Thing
at all.
I wanted to install bmpX and it wasnt in Synaptic.[/QUOTE]
Ok, but my questions above stand.  Particularly 3) Is there a file called README or INSTALL?

> 
I cant do the:
./configure
make
make install
Thing
at all.
In what way "can't do"?  What errors do you get?

---

### Post by qferret on 2006-01-16
If you just type sh and hit enter does your prompt change?

It should change to sh-3.00$ or similar. At this point you can enter shell commands directly (e.g. echo test <enter> exit <enter>)

Just wondering if sh is actually working for you....

---

### Post by shade11 on 2006-01-16
It does change to sh-3.00#.

---

### Post by PuNGS on 2006-01-16
Have you already download the build-essential library?

```
sudo apt-get install build-essential
```

---

### Post by qferret on 2006-01-16
whoopsie...missed page 2 of the thread the first time through....we're past the shell script thing LOL

Sorry... li'l slow tonight

OK...as RAOF asked, what errors do you get when going through the configure/make/install process?

is ./configure working? (assuming your prompt is in the source directory)

---

