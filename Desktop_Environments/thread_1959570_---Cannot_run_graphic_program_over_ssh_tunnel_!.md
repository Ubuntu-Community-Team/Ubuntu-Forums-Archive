---
title: "---Cannot run graphic program over ssh tunnel !"
date: 2012-04-16
forum: Desktop Environments
---

### Post by bzhao on 2012-04-16
I am not sure if here is good place to put my question.


I use "ssh -Y -p 2222 access myserver_name" to access my server.

and I often run "bless", "bcompare", etc at the ssh teminal and see the graphic result on my local ubuntu desktop.

This morning I found that I cannot do that. the run program exit and the error info on the termial is: 
     Gtk-WARNING **: cannot open display:

I tried to recall what I have done to the server, and tried to remove some changes I have done. the result is the problem is still there.

In an addition I have another server which run the same version of Ubuntu 11.04 as the one I have the problem with. it work very normally. I also compare the config file between the 2 server. I cannot see what problem is.

I also see the log in /var/log/syslog file, no erro info there

I am going crazy for the problem! I really need to run graphic program remotely!

Please help how to debug the problem.  

Thank indeed!

Bill Z

---

### Post by markbl on 2012-04-16
> **bzhao said:**
> 
I use "ssh -Y -p 2222 access myserver_name" to access my server.

What is "access" in the above command? Hopefully some typo.

Anyhow, after you ssh in to that server using the above command then type the following at the myserver_name command line:
```

echo $DISPLAY

```
That may give you a hint to the problem.

---

### Post by Irihapeti on 2012-04-16
You need to include the option -X in your command to forward X.

If you're using connections regularly, it can be worth setting up launchers. I have several launchers set up for particular programs that I use on my LAN at home. The commands look like:

```
ssh -f -T -X foo /path/to/program
```

"foo" is shorthand for the connection information and is defined in ~/.ssh/config like this:

```
Host foo
 HostName yourmachinename (you can use IP address instead)
 Port 55555
 User yourname
```

When you connect, it will ask you for your password, or your ssh key passphrase if you are using keys.

---

### Post by bzhao on 2012-04-16
Thanks for your responses!

For debugging in ssh terminal:

"echo $DISPLAY"  give me nothing of printting, 

while I got "localhost:11.0" on my normal server.

then I try run "exprort DISPLAY=localhost:11.0",
and then I still have the same problem. error info is still the same:
"(bless:12785): Gtk-WARNING **: cannot open display: localhost:11.0"

---

### Post by markbl on 2012-04-16
Did you add the -X as suggested above? I personally just add "ForwardX11 yes" to my ~/.ssh/config in the global top section.

Make sure "X11Forwarding yes" is set in your servers /etc/ssh/sshd_config. Run "sudo service ssh restart" after you change that file.

You can't just manually set DISPLAY. It must be set automatically by ssh then you know the X tunnel has been set up.

---

### Post by bzhao on 2012-04-17
> **markbl said:**
> Did you add the -X as suggested above? I personally just add "ForwardX11 yes" to my ~/.ssh/config in the global top section.
[COLOR="Blue"]I did try -X funtion, it did not work.[/COLOR]
[COLOR="Blue"]I also add a line of "ForwardX11 yes" in /etc/ssh/ssh_config, it does not work eighter[/COLOR] 

Make sure "X11Forwarding yes" is set in your servers /etc/ssh/sshd_config. Run "sudo service ssh restart" after you change that file.
[COLOR="Blue"]
Yes, Ubuntu ship ssh with it as default.[/COLOR]

You can't just manually set DISPLAY. It must be set automatically by ssh then you know the X tunnel has been set up.
[COLOR="Blue"]Yes, I got it[/COLOR]

---

