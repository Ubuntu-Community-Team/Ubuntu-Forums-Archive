---
title: "How to automatize restart of LightDM"
date: 2012-10-14
forum: Desktop Environments
---

### Post by le_phoceen on 2012-10-14
Hello everyone !

For one week or so, after an update of Xubuntu 12.04 on my Acer Aspire One, I have had some big display problems. Namely, only the upper half of the screen works on the LightDM greeter screen and after in the xfce session.

I'm able to make it all work normally just by switching to text mode and restarting LightDM with this command : ```
sudo service lightdm restart
```

However, I'm getting tired of doing this workaround anytime I boot my netbook and I would like it to be automatized at every boot.

Does someone know how I can do this ?

Many thanks :)

---

### Post by firekage on 2012-10-14
Have you got an nvidia card onboard this Acer laptop?

---

### Post by Insomn1a on 2012-10-14
make a text file and input that command that you want, save it as whateveryouwanttocallit.sh put it in a location thats easy to find.

> 
nter ALT F2 and enter: gksu gedit /etc/sudoers  and press enter.

and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: scriptpath
-------------------------------------------------------------------
BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME.
and replace scriptpath with the path to the file you want to run without a password.

for example, I want the script to run at startup as sudo without typing in the password. The last line in my file looks like:


jeroen ALL= NOPASSWD: /home/jeroen/wifi-on.sh

where "jeroen" is my user name and "/home/jeroen/wifi-on.sh" is the script i want to run.

now save the file and close it. you are now allowed to run your script as sudo without typing in a password.

so go to system > preferences > sessions and add the command you want to run at startup under "startup programs", mine looks like:
gksu /home/jeroen/wifi-on.js (replacing the path with the path to your script).

Reboot and configure your Wifi.
Reboot again and the machine should go online automatically. Even better than Windows Vista does.


Source: [https://sites.google.com/site/installationubuntu/tweaking-ubuntu/automate-sudo-commands-at-startup](https://sites.google.com/site/installationubuntu/tweaking-ubuntu/automate-sudo-commands-at-startup)

---

