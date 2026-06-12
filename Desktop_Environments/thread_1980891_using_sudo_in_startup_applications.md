---
title: "using sudo in startup applications"
date: 2012-05-16
forum: Desktop Environments
---

### Post by sshanky on 2012-05-16
Hi,

I'm running a digital signage ubuntu 12.04 desktop machine. I need an application to start (graphical, not a service) when the machine starts up or restarts. The application has to run as root. I've learned how to [add the appropriate entry to sudoers]("http://greeennotebook.com/2010/06/run-application-as-root-at-startup/") so that it does not need to ask for a password, ever, and I have tried to add the word "sudo" to the command in the Startup Applications program. It works the first time I restart, but then, when I look at the Startup Applications entry, the "sudo" is gone from the command entry. To be more specific, I edit the startup programs entry, and put:

sudo /home/username/rvplayer/rvplayer

into the "Command:" field. Then I restart, and the rvplayer applications launches properly. But, if I restart again, it won't start automatically. When I re-check the entry in Startup applications, I see:

/home/username/rvplayer/rvplayer

(without sudo). Is there a better way? Am I doing something wrong?

Thanks a lot!

---

### Post by markbl on 2012-05-16
Requiring an app to run as root is not a good design but I guess you don't want to hear that.

Using sudo is not the way to go here. Firstly, given that app should run as root you should move it (just for neatness):

```

mv /home/username/rvplayer/rvplayer /usr/local/bin/

```
You can just start that app from /etc/rc.local at boot time (that runs as root user). Or you can do something like:

```

sudo chown root:root /usr/local/bin/rvplayer
sudo chmod +s /usr/local/bin/rvplayer

```

That sets it owned by root and setuid. Google setuid to understand this.

---

### Post by roelforg on 2012-05-16
If you know what you're doing, you could modify sudoers to allow you to sudo that cmd w/o asking for a pass, as i suspect that's the prob.

---

### Post by sshanky on 2012-05-16
> **markbl said:**
> Requiring an app to run as root is not a good design but I guess you don't want to hear that.

Using sudo is not the way to go here. Firstly, given that app should run as root you should move it (just for neatness):

```

mv /home/username/rvplayer/rvplayer /usr/local/bin/

```
You can just start that app from /etc/rc.local at boot time (that runs as root user). Or you can do something like:

```

sudo chown root:root /usr/local/bin/rvplayer
sudo chmod +s /usr/local/bin/rvplayer

```

That sets it owned by root and setuid. Google setuid to understand this.

Thanks for the reply. I know it's not the best thing to run it as root -- I would rather not have to. I just need rvplayer to start on its own. When I don't run it with sudo I get an error about permissions being denied. I could try to figure out how to fix this from another angle, but I was hoping this would be easier.

I read that I can't use /etc/rc.local to start the app as it would run it as a service -- and this is a chromium browser based thing, so I think it's necessary to wait until the gui is loaded, right?

I don't understand the chown/chmod solution, but it appears to be closer to what I would want to do -- does changing the user under which the app runs have a chance of making this work?

Thanks a lot, again. I am about to try changing some permissions on the folders that can't be written to without sudo. Maybe that will resolve it.

---

### Post by markbl on 2012-05-16
> **sshanky said:**
> 
I don't understand the chown/chmod solution, but it appears to be closer to what I would want to do -- does changing the user under which the app runs have a chance of making this work?

You change the executable file to be owned by root then set the "setuid" bit so that the file executes with the permissions of the  owner. As I said, google it. First link comes as wikipedia and seems to explain it pretty well.

---

### Post by sshanky on 2012-05-16
Ah, that makes sense. Thank you!

---

### Post by sshanky on 2012-05-16
Hi again...I think I understand this. This morning, even if I sudo chmod 6711 rvplayer, (-rwsrwsrw-) and changed its group and owner to root, it couldn't start (permission denied) because it didn't seem to have sufficient permissions to write to a settings file that has very reduced permissions set. sudo worked fine. I ended up just chmodding the ~/.config/rvplayer and the entire application directory to 777 for the time being, and then it worked.

I had thought the app would have root privileges, since it's group and owner are root, and the permissions are now set as shown above.

Thanks.

---

