---
title: "Making a Command Run upon startup"
date: 2009-06-07
forum: General Help
---

### Post by rasmus91 on 2009-06-07
Hi

I was just wondering if somebody could tell me how i can make a command running upon startup, By creating a autolaunching bash script or whatever?

Please tell me, as this would be very very useful to me.

---

### Post by -kg- on 2009-06-07
What type of command do you want to run on startup?  Or are you trying to launch a program?

If you're trying to launch a program, you can do so through "Applications/Settings/Session and Startup."

I'm not so sure on actually launching a command.  Like you said, you may need to write a bash script with the command and include it under "Sessions and Startup" under the "Application Autostart" tab.  I notice that, in my case, there's one script included, so you should be able to add your script for execution at startup.

---

### Post by Baelus on 2009-06-07
```
sudo nano /etc/rc.local
```

The file has comments that explain a bit about it.

Add your commands to the script above the "exit 0" line.

To save and exit press F2, hit "y" then "Enter".

Make the script executable with:

```
sudo chmod +x /etc/rc.local
```

That should have your commands run when things boot up.

If launching a gui program, use the method -kg- suggested.

---

