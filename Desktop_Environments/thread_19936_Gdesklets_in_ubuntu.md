---
title: "Gdesklets in ubuntu"
date: 2005-03-14
forum: Desktop Environments
---

### Post by symbiont on 2005-03-14
Ok...did some searching, can't find the answer

Installing gdesklets in Ubuntu....some of the sensors i grab from the gdesklets website have a .bin file to install the sensor. When i run the bin file...it pauses and then blasts a bunch of errors and fails to install

Install_iWeather_Sensor.bin: line 18: ERROR_B64: command not found
Install_iWeather_Sensor.bin: line 20: ERROR_TAR: command not found
Install_iWeather_Sensor.bin: line 22: SUCCESS: command not found
Install_iWeather_Sensor.bin: line 27: no_message: command not found
Install_iWeather_Sensor.bin: line 28: list_only: command not found
Install_iWeather_Sensor.bin: line 29: destination: command not found
Install_iWeather_Sensor.bin: line 32: args: command not found
Install_iWeather_Sensor.bin: line 34: syntax error near unexpected token `if'
Install_iWeather_Sensor.bin: line 34: `    if (p == "--nomsg"): no_message = 1'


Anyone know what the problem is?

---

### Post by Xian on 2005-03-14
[QUOTE=symbiont]Anyone know what the problem is?[/QUOTE]
What version of Gdesklets are your using? You should just be able to use the Gdesklets shell to install, remove, and manage all the desklets. If you are having to use a workaround then most likely those desklets are obsolete.

---

### Post by symbiont on 2005-03-14
[QUOTE=Xian]What version of Gdesklets are your using? You should just be able to use the Gdesklets shell to install, remove, and manage all the desklets. If you are having to use a workaround then most likely those desklets are obsolete.[/QUOTE]

I am using the most recent version of Gdesklets from the 'universe' repositories...I'd have to check when i get home to be sure what the ver number is.  How do you use gdesklets shell to install?

---

### Post by Joeb on 2005-03-14
Are you running Warty or Hoary?  I've had a lot of problems with the Gdesklets that's in Hoary.  Mainly, in the scripts error out, though, not in installation problems like you are having.

Joeb

---

### Post by Xian on 2005-03-14
[QUOTE=symbiont]I am using the most recent version of Gdesklets from the 'universe' repositories...I'd have to check when i get home to be sure what the ver number is.  How do you use gdesklets shell to install?[/QUOTE]
If you are running the Universe version it most likely will support using the Gdesklets shell to manage your desklets. The only thing you need to set up before using the shell is to confirm that you have a notification applet running in your taskbar, as that is where the daemon will reside once you issue the run command.

Applications > Run Application > gdesklets shell

Then right click on the Gdesklets daemon in your taskbar and choose "Manage Desklets".
Then from the shell window: File > Install Package

Once added, select a set of desklet groups in the Category window and double-click on a specific desklet to run it, using your mouse pointer to position it on your desktop.

---

### Post by symbiont on 2005-03-14
hmm...i have gdesklets version 0.26.2 off of the universe repositories.  Guess that might be why its not working right.   :D

---

### Post by Xian on 2005-03-14
[QUOTE=symbiont]hmm...i have gdesklets version 0.26.2 off of the universe repositories.  Guess that might be why its not working right.   :D[/QUOTE]
I'm using the Hoary version of Gdesklets and it runs the daemon just fine, but when I was in Warty I just compiled version .33 from source, and I can verify that all the devel-libs you need are right in the non-universe Warty repo. Anyway, that is definitely an option for you and it worked on my box.

---

### Post by symbiont on 2005-03-14
ok thx...will try that and let you know

---

### Post by Xian on 2005-03-14
[QUOTE=symbiont]ok thx...will try that and let you know[/QUOTE]
Start the ./configure process and each time you get an error look for what package it is referencing. Go ahead and keep Synaptic open so you can do a search for the needed libs, and just install them as you go along. It will finish with no problem after you satisfy the few deps that you come across.

---

### Post by symbiont on 2005-03-14
yeh i;m in the process of doing that.

but i get 

configure: error: Can't find Python.h! You will need the python development package
              to successfully compile gDesklets.


and i do have python 2.3 installed, so again i'm stuck

---

### Post by kassetra on 2005-03-14
[QUOTE=symbiont]yeh i;m in the process of doing that.

but i get 

configure: error: Can't find Python.h! You will need the python development package
              to successfully compile gDesklets.


and i do have python 2.3 installed, so again i'm stuck[/QUOTE]

Do you have the python-dev 2.3 installed?

---

### Post by Xian on 2005-03-14
[QUOTE=symbiont]yconfigure: error: Can't find Python.h! You will need the python development package to successfully compile gDesklets.

and i do have python 2.3 installed, so again i'm stuck[/QUOTE]
Actually, you got a break there as it usually doesn't get so precise. 
But as has been said, look for those dev packages.

Post back with any other problems....

---

### Post by symbiont on 2005-03-14
welp finally installed and running.  I went through the configure many times installing many dev packages and the newest version .0.34 still keep erroring.  So I dropped back and installed the 0.33 ver you had working...and its running fine.  Gdesklets are installing fine fo the most part...except the one i wanted to run called Qstat.  But i think something is wrong with that display in particular because every other one i;ve installed is fine.  thanks for the help all.

---

### Post by Xian on 2005-03-15
Hey, that's great to hear. And yeah, there are some desklets still available for download that just won't work anymore with the newer releases. But the advantage in using the shell to manage and start everything is a much easier aspect to that application.

---

