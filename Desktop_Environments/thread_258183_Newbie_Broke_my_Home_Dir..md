---
title: "Newbie: Broke my Home Dir."
date: 2006-09-15
forum: Desktop Environments
---

### Post by DennShin on 2006-09-15
Hello Everyone, 
   I am very new to Linux and I am hoping that someone else has made the same mistake as I and know's how I may correct it.  I was trying to make change's to a file in my etc/x11 directory and was given the error that I did not have permission.  I thought I may remedy this by setting my home directory to that directory. (That didnt work of course).  So I set myself back to what I thought was my home home directory.  However.  On reboot I get the following error.  "Your home directory is listed as '/home/dennshin/desktop' but it does not appear to exist.  Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session".  Now I have tried using a failsafe session to see where I went wrong but I recieve another error that says my session has lasted less than 11 seconds and will restart.  So my questions are.  #1 Is their a way to set my home directory from the terminal? and #2 Is not the default directory /home/username/desktop?  

Thank you for helping a newbie like me out.  I paitently wait your answers.

---

### Post by skierkegaard on 2006-09-15
I know in the bash shell you can edit env.  This contains your home directory in a variable called HOME.  The default directory of a user should be /home/username, not /home/username/Desktop

---

### Post by DennShin on 2006-09-16
Ok, I got this working.  For anyone else who may need this information.  At the recovery console enter. 

sudo pico /etc/passwd 

on the following screen go to the last line and edit your home directory 

Ctrl+X to exit then Y to save then Enter 

Restart and you should be up and running again.

---

