---
title: "Desklets"
date: 2005-12-16
forum: Desktop Environments
---

### Post by jabb0 on 2005-12-16
i have been messing around with both the a & g flavours on gnome.

I never managed to get the adesklets to work. I had compiled them from source and ran into the infomous flicker problem and couldnt shift it, before i realised that is ctually available from one of the repoistories.
The thing is i would like to remove the original adesklets i compiled and installed and try again using the one from the repository - but i have no idea how to go about such a task, can it even be done?

Another thing happened me too, i had my desktop all sittin pretty, took me ages, and then i start my box up the other day and when i started gdesklets it didnt place any of the desklets on the desktop automagcally like all the other times.
I dont want to spend an age setting my desktop up every time i start it. Its not normal behaviour, gdesklets usually remembers stuff like that. any ideas?

---

### Post by Ampersand on 2005-12-16
For the first problem, a 
```
sudo make uninstall
```
in the adesklets source directory might work.

For the second one, it might be worth saving your setup as a new profile in the gdesklets manager once you have it to your liking. Hopefully then you'll have more chance of being able to find it if it doesn't load automatically.

---

### Post by jabb0 on 2005-12-17
gosh its all so simple when you know how, ur a :KS mate.
I thought it might be an idea to read the documentation for gdesklets, and ooo did i get a surprise.  The thing is pretty thouroughly doc'ed, i think i might try make one.

Thanks for the make uninstall thing - makes me feel a bit like a Dime Bar.

hey u know the way the 3 commands 
- configure
- make
- make install
always go together when u compile and install something, well i kinda know that configure gathers info about ur linux install, but if "make install" actually installs the thing what does "make" do?

just tried the make uninstall thing, it jus complained - not to worry too much tho, ive got the whole reinstalling thing down to under half an hour now - aye windoze stick dat in ur pipe an smoke it

---

### Post by bonzodog on 2005-12-17
when you get a program like that, it is in raw C code - 'make' compiles the code into the binary so the computer can run in. 'configure' tells the make prog what your machines set-up is, and make install just installs the binary. However, in Ubuntu, you can do a 'make checkinstall', which compiles the program and installs it as a .deb that synaptic can see. also, if you do this and have compiled the only version, you can then realease it as a deb for others to use.
I have written a guide on program installation routines here:

[http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners)

---

### Post by jabb0 on 2005-12-17
jees u learn something new everyday, and this day is prooving to be quite informative.
 Nice guide mate, thats gonna save me alotta hassle in the future.
 
 Would it be possible to write a program in c and compile it on both windoze and linux or any platform for that matter?
 
 tis jus im a bit of a hacker and after php i wanted something new to  try out and c looked interesting.

---

### Post by jabb0 on 2005-12-18
back on the adesklets thing, i have made some progress however the system monitor script i am trying to run dies out at line 43 where it is trying to import statgrab.
I have installed statgrab its there i can see it but this just wont work.

I was thinking i would rewrite that line and tell it where statgrab is, but alas i connot find a file called statgrab - libstatgrab yes, but not statgrab.

any ideas/

---

### Post by freakzilla on 2006-01-01
I'm working on getting the system monitor adesklet functioning also.  I get the same error as you.  The program tries to import statgrab and fails.  

I think the problem is system monitor needs pystatgrab-0.4 installed.  I haven't figured how to do that part yet.

---

