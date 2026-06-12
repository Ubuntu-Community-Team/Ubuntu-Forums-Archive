---
title: "No Wifi, no su/sudo, no USB boot, no clue"
date: 2019-06-15
forum: Desktop Environments
---

### Post by meshica7 on 2019-06-15
Help please!!!

Recently I have encountered a slew of issues with Kubuntu 19.

I purchased an Acer laptop and did a clean instal of Kubuntu 18. I eventually upgraded to 19.04 and not long after, my main acct in Kubuntu had developed issues with notifications taking up the whole screen. I tried everything I could think of to no avail. So, I created a guest acct (admin, or so I thought) and the issue did not replicate. I figured it was related to the original acct. So after trying everything suggested in the forums at Going Linux with no success I decided to (and bear with me as even though I have been using Linux off and on for 15 yrs now, I am no super user by any means) delete the original acct that was created when I installed Kubuntu from USB. Of course this was stupid on my part as I now have no **sudo** access to anything. I simply did not think about that assuming that creating a guest acct with admin priv would be the same. I tried **sudo** commands in the term and nothing..no access..denied! So I uninstalled KDE and related packages via MUON (I had installed Xubuntu previous to this) in hopes of deleting whatever may have been causing all the fuss with the bloated notifications and other graphic anomalies such as large task bar which I had to resize every time I logged in. Once I deleted KDE and reinstalled it via MUON, I rebooted. Now I have lost my Wifi connectivity. I tried everything..Network Preferences, made sure airplane Mode was disabled, made sure that the battery saver was not engaged..everything. My WiFi doesn't show up at all. Grrrrr. So..I was willing to do a fresh instal from USB. No problem. Except now the option for booting from USB does not appear in my BIOS...anywhere. So I am stuck with a no wifi, no USB bootable laptop running a non root (**su** and **sudo** prompts do not work) 19.04 Ubuntu. I really do not know what to do! I am writing this from my old MacBook..wanna get back on my Linux Laptop ASAP!
My endgame here is to get the laptop to boot from USB..that way I can at least instal a fresh Ubuntu in hopes of reinstalling the necessary components from the fresh ISO so I can use my WiFi again. I tried to reinstall them via term but without su privys I was not able to do this. It's a Catch 22! No wifi: No ISO download (at lest I can do that on my Mac) AND no USB Boot; No fresh instal..grrrrr. I am about to toss this laptop at the wall! LOL. No..I won't..I just wanna get this sorted out.:mad:

---

### Post by TheFu on 2019-06-15
Ouch.  I've removed my sudo abilities a few times, but nothing so bad as you describe. 
I don't haven't any definite answers, just things to check out.

So ... USB booting isn't controlled by the OS.  That is a BIOS thing.  Look into the BIOS for anything that would prevent USB booting.

Let's try some simple things.  Try a different USB flash drive.  Try a different USB port on the laptop.  I've had laptops that would never boot from USB3 ports, but always worked from USB2.  They also worked from SDHC card slots if you have one of those.

The flash drive you have with a DESKTOP version of Ubuntu?  Did it boot from that specific device at any point before?  You can create a fresh boot flash drive on OSX, BTW.  There are instructions here: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos)

So, after you boot a DESKTOP Ubuntu system, choose "**Try Ubuntu**" or whatever the variant you are using happens to be Lubuntu/Xubuntu/Ubuntu-Mate all work well.  From here you can mount the internal HDD/SSD, find the /etc/group file and add the new userid - admin? - to the sudo group.  Do this by finding the line with sudo in that file and adding a ",admin" to the end of the line.  I'd say to use **sudoedit /whatver/the/mount/path/etc/group **is so you safely edit the file.  If you make any mistake, really bad things can happen. In my system, the group file line looks like this:
```
sudo:x:27:thefu
```
While you are there, it would be good to add the prior "1st login" account back too.  On desktops, many services are tied to that account.  

BTW, instead of using wifi, why not just plug into the network using an ethernet cable?  That should always work, regardless of the users available.  Wifi connections are often tied to specific accounts.

I'm a little worried about having a user account named "admin".  There is already a group on every Unix system with that name. While I don't have firm reasons why it is not a good idea, I can see potential issues coming in the future from using it.  *admin01* would be 1000000x better username. No system accounts like it exist.

Thanks for running the non-LTS systems. You are braver than me.  I did my bleeding-edge time in the 1990s when there wasn't any other choice.  These days, I'm rockin' 16.04, probably until 2021 on all my systems - desktops and servers.  New is the enemy of stable.

---

### Post by mc4man on 2019-06-16
Have you tried
[https://au.answers.acer.com/app/answers/detail/a_id/7550/~/changing-boot-order](https://au.answers.acer.com/app/answers/detail/a_id/7550/~/changing-boot-order)

---

