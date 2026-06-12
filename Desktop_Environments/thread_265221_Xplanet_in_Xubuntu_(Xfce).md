---
title: "Xplanet in Xubuntu (Xfce)"
date: 2006-09-25
forum: Desktop Environments
---

### Post by scott_b on 2006-09-25
Here's how I got xplanet to work on Xubuntu, I guess it'll work on any ubuntu running xfce.  
This will give full use of desktop and transparency in xfce4-terminal

1) Install Xplanet and xplanet-images
```
sudo apt-get install xplanet xplanet-images
```

2) Run Xplanet.
[INDENT]It is important that you have "-output /pick/a_place/xplanet.png" somewhere (it doesn't have to be *.png), and the "-wait X" (where X=seconds) to regenerate the file at the desired intervals. Other than that, you can customize in the regular xplanet fassion (man xplanet).  
Mine reads:[/INDENT]
```
xplanet -projection mercator -geometry 1024X768 -output /pick/a_place/xplanet.png -wait 60
```
[INDENT]Note: you will not see xplanet running[/INDENT]

3) Choose the Xplanet output image as your desktop image.  
[INDENT]I'm not sure if you need to, but I put my xplanet.png as the only image in the backdrop list. 
Menu -> Settings -> Desktop Settings -> "New List"/"Edit List" -> etc. etc.-> /pick/a_place/xplanet.png -> etc. ect.[/INDENT]

4) The kicker. Set up a cron job that will get Xfce to refresh its look at the image put out by xplanet.
```
crontab -e
```
```
# m h  dom mon dow   command
0,5,10,15,20,25,30,35,40,45,50,55 *     * * *   export DISPLAY=:0; /usr/bin/xfdesktop -reload
```
[INDENT]This will refresh the image every 5 minutes.  A bit much.  The important part is "export DISPLAY=:0; /usr/bin/xfdesktop -reload".[/INDENT]

5) Run Xplanet on Xfce start-up.
[INDENT]-Menu -> Settings -> Autostarted Applications
-Click "Add"; pick a title and description.
-In "Command" you tell Xplanet to generate a image using your preferd command (above).  Make sure that the fields for "output" and "wait" are present.[/INDENT]

Edit 1: I should note that I have experienced irregularity after I resume from suspend.

Edit 2: When you log in, run ps -e to determine how many xplanet's you have running.  if its more than one, take the appropriate steps to reduce the number to 1 on future logins.  If you have more than one running, there will be occasional black-outs on the desktop.

---

