---
title: "Ubuntu 18.04 WD ShareSpace NAS...On my Desktop..."
date: 2018-11-30
forum: Desktop Environments
---

### Post by SolomonMan on 2018-11-30
All,
I have used Linux on and off for about 20 years now...including a long stints during my CS Masters Degree...but by no means a expert I am a programmer...LOL.

Anyways, I have a WD Sharespace NAS that I got from a decommissioned NAS at work...Its like a 4GB unit.

I put in some new larger drives in it (originally it was 3GB) and it works great on the Windows side and has this one thing I can not figure out in Ubuntu.

On my Ubuntu box I can use the file manager and then Windows Share icon...I can see the NAS icon...I click it but its a configuration file (not the actual share I setup)...So after a few minutes of trial and error I pressed Ctrl +L and I edit the path which is initially smb:\\<actual ipaddress>\    to  smb:\\<actual ipaddress>\sharefolder\ and boom I can access the created share including saving files etc. (Originally it popped up a credentials window for the NAS I entered and said remember and then we are good...never seen the credential window going forward as expected.)

I tried to setup a symbolic link to my Desktop and boom it worked as I hoped...Unfortunately upon reboot all is gone...and I still have to go through the windows share icon under the File Manager and do all the above steps again...

Thru trial and error.... I tried to mount the NAS in the etc/fstabs file and included the user name and password and still no luck.

So I know the system can use the drive but I just do not want to go thru the above steps over and over...I have at least 4 machines to do this to...not including laptops.

Does anybody know the way to mount the NAS drive share to show it on my Desktop folder?

Thanks
Chris

---

### Post by Morbius1 on 2018-11-30
If you are otherwise happy with the way the file manager connects to the share you could use Gigolo ( sudo apt install gigolo ).

You would access the share using the Connect to Server function in gigolo: Actions > Connect

Once connected you create a bookmark by right clicking the mounted share within gigolo and selecting: Create Bookmark

[ATTACH=CONFIG]281834[/ATTACH]

Then have gigolo start at login by adding it to your "Startup Applications" with the command: gigolo

Logoff and login again and your share if the nas is present will be mounted. If your nas for some reason is not running when you log into your system gigolo will wait until it is available then it will mount the share.

It took me longer to write this post than it will take you to familiarize yourself and use gigolo.

---

