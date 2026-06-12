---
title: "Start ircd automatically"
date: 2009-04-25
forum: General Help
---

### Post by Musicalmidget on 2009-04-25
Having just done a clean install of Ubuntu 9.04, I've installed IRSSI and Bitlbee as I did on my previous system, including following the instructions on the [Bitlbee Community Documentation](https://help.ubuntu.com/community/Bitlbee) page.  Both IRSSI and Bitlbee are working fine but each time I restart my machine, the local IRC server goes offline and does not restart automatically, meaning I have to reload xinetd before attempting to connect to localhost and use Bitlbee.

I don't recall having this problem previously and so don't have any past experiences to work from.  I gather that I need to somehow tell the ircd to start each time Ubuntu boots but I'm not sure how to do that.  I suspected it might be a case of setting up a command to run on boot in System > Preferences > Startup Applications, but I'm not sure which command would be most suitable.  Perhaps the xinetd reload command or something better?

Any suggestions would be very much appreciated, as always.

---

### Post by pytheas22 on 2009-04-25
I don't know anything about IRC servers, but I suspect that the best way to start it automatically would be to [write a boot script]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") in the /etc/init.d directory (that link should explain what you need to know, but if you have questions, feel free to post).  You can just write a script and put in it whichever command(s) you use to start ircd manually, and the system should run them automatically at boot.

The System>Preferences>Sessions utility is meant for starting applications that are used by the individual user, not by the system as a whole.  You probably could use it to do what you want, but it would not be a good solution.

---

### Post by Musicalmidget on 2009-04-26
I've had a go at writing a boot script to reload xinetd but I don't seem to have had any luck.  I don't know if it's because the command needs to be run by root or with sudo and maybe boot scripts aren't able to do this?  Is that likely to be an issue?

---

### Post by pytheas22 on 2009-04-26
The boot scripts are all run by root, so that's not the problem.  Which commands did you put in the script?  Did you put *#!/bin/bash* as the first line in the file so the system knows how to run it?  This might be necessary.  You should also check to make sure the system is executable; if it's not, you can make it so by typing:
```

sudo chmod +x /etc/init.d/SCRIPT-NAME
```

Finally, make sure you used the 'update-rc.d SCRIPT-NAME defaults' command to tell the system to run it at boot.

---

### Post by Musicalmidget on 2009-04-26
I had #!/bin/sh at the start of my script, but I've changed it to #!/bin/bash and there's no change.  I've tried both the xinetd reload and restart commands, with and without sudo.  The script is executable and the system startup links created by using update-rc.d.  It just seems as though nothing seems to work.

Just for reference, here's the current version of the script.

```
#!/bin/bash
/etc/init.d/xinetd reload
```

---

### Post by pytheas22 on 2009-04-26
Try adding a line like this to the end of the script:
```

touch /home/YOUR-USERNAME/Desktop/the-script-ran
```

Then reboot.  If the script runs, there will be an empty text file on your desktop named 'the-script-ran'.  If there's no file, then we know there's a problem with the startup links or permissions on the script.  If the file does get created, then it's most likely a problem with the command you're using to try to start ircd.  What's the result?

---

### Post by Musicalmidget on 2009-04-26
Great idea.  When I reboot the machine I see the touched file on my desktop so evidently the script is running, but it's not having the desired effect.  Strangely, running exactly the same command manually from a terminal window does then work, so I can't seem to figure this one out.

Any idea what else I could try?

---

### Post by pytheas22 on 2009-04-26
That's strange.  If you change your script to this:
```

#!/bin/bash
/etc/init.d/xinetd reload > /home/YOUR-USERNAME/Desktop/output.txt
```

it will save the output from trying to run the command into a text file on your desktop named 'output.txt'.  If there's an error message being produced when the command tries to run, you should see it there.  Anything?

---

### Post by Musicalmidget on 2009-04-26
It would appear that the script is running without problems.  This is the content of the output file.

```
 * Reloading internet superserver configuration xinetd
   ...done.
```

I started wondering if xinetd was perhaps causing the issue, so I completely purged and removed both xinetd and bitlbee to start from fresh.  I've since reinstalled bitlbee only and discovered that bitlbee includes a boot script for starting the bitlbee daemon without requiring xinetd.  The catch however, is that the same thing happens only with a different command.  With this method, irssi fails to connect to localhost until I start /etc/init.d/bitlbee.  Different command, same problem.

---

### Post by pytheas22 on 2009-04-26
This is indeed strange, but interesting.  I wonder if perhaps the default startup priority given to the script is not what it needs.  If you run this command, it will be run at the end of the startup sequence, which may work better:
```

sudo update-rc.d SCRIPT-NAME start 99 2 3 4 5
```

Any difference?

Also, after boot finishes but before you start ircd manually, do you see the process listed if you run 'ps -e | grep ircd'?

---

### Post by Klaz168 on 2009-04-26
I guess it's simpler than that, how about a bash script that launches your IRCd after booting, saves an entry of it in a log file?

#!/bin/bash
sleep 10
~user/Unreal3.2/unreal start #suppose you have unreal
echo "Unreal3.2 started: $(date)" >> ~user/Unreal3.2/unreal.start.log
echo

---

### Post by Musicalmidget on 2009-04-26
> **pytheas22 said:**
> This is indeed strange, but interesting.  I wonder if perhaps the default startup priority given to the script is not what it needs.  If you run this command, it will be run at the end of the startup sequence, which may work better:
```

sudo update-rc.d SCRIPT-NAME start 99 2 3 4 5
```

Any difference?

Great stuff, this is working fine.

Many thanks for the help.

---

