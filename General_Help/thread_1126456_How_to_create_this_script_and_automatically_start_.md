---
title: "How to create this script and automatically start it?"
date: 2009-04-15
forum: General Help
---

### Post by rams123 on 2009-04-15
Hello everyone,

**First thing I do after installing ubuntu:**

[LIST]
[*]Open Network Manager, enter my Static IP, and save it.

[*]After I connected to network, I download one folder(**crclient**) from local ISP server.(If you don't understand, just leave it)


[/LIST]
Then I open Terminal, and enter the below two commands to login (after login I can access internet):

```
cd Desktop/crclient
```
*[SIZE="1"]then[/SIZE]*
```
./crclient -u rams
```

After entering the above commands I get a message, you've sucessfully logged in, after that I can browse the net.
 
===========
But the problem is every time I start my PC, I have to enter those two commands manually in Terminal to access internet.

I've also tried by adding that two commands to auto-start(in session manager)

Like this: **cd Desktop/crclient;./crclient -u rams**. But no luck, it's not working :(

==========
Is there any way to write a script that will run those two commands when open it? So that I can add that in auto start or at least I can run thaose commands with single click..

***Guys, I need your help..***

---

### Post by Alekz_ on 2009-04-15
Hi rams! :)

Just put this lines into a text file:

#!/bin/sh
. ~/Desktop/crclient/crclient -u rams

and save the file.

e.g:
login_ISP.sh

After you save it, give the file execution permission:

chmod +x /your/path/login_ISP.sh

And you can execute the file!

You may want to auto-execute on start-up, so you add the login_ISP.sh under auto-start (session manager)

[]'s

Alekz_

---

### Post by iponeverything on 2009-04-16
You also add the static ip address info to /etc/network/interfaces
and have you crclient prog ran from there. Copy crclient to /usr/local/bin make sure its executable and something this stanza to /etc/network/interfaces/ (the ip information will be your own)


```
iface eth0 inet static
            address 192.168.1.10
            netmask 255.255.255.0
            gateway192.168.1.1
            up /usr/local/bin/crclient -u rams

auto eth0

```

At which point it will come up on its own.

---

### Post by rams123 on 2009-04-16
Thanks Alekz_ :)

> **iponeverything said:**
> You also add the static ip address info to /etc/network/interfaces
and have you crclient prog ran from there. Copy crclient to /usr/local/bin make sure its executable and something this stanza to /etc/network/interfaces/ (the ip information will be your own)


```
iface eth0 inet static
            address 192.168.1.10
            netmask 255.255.255.0
            gateway192.168.1.1
            up /usr/local/bin/crclient -u rams

auto eth0

```

At which point it will come up on its own.

OK. But what is the use of doing this? Could you please explain me what that will do?

And I've already configured my IP details in "Network Configuration", so what the use of adding the same thing in /etc/network/interfaces?

---

### Post by kpkeerthi on 2009-04-16
Thats a cool tip from iponeverything.

What it helps achieve is run the crclient script automatically when you connect to the network.

Putting the script in session manager will not help, since you want the script to be run 'after' you are connected to the network.

```

cd Desktop/crclient
sudo cp crclient /usr/local/bin
sudo chmod +x /usr/local/bin/crclient

```
and then add
```

up /usr/local/bin/crclient -u rams

``` to /etc/network/interfaces as explained in the above post

---

### Post by Alekz_ on 2009-04-16
Make sense!

Really good tip! :)

---

### Post by kpkeerthi on 2009-04-16
> **rams123 said:**
> 
And I've already configured my IP details in "Network Configuration", so what the use of adding the same thing in /etc/network/interfaces?

Your /etc/network/interfaces should reflect what you have configured using the GUI. You don't have to repeat the same thing.

---

### Post by rams123 on 2009-04-16
> **kpkeerthi said:**
> Your /etc/network/interfaces should reflect what you have configured using the GUI. You don't have to repeat the same thing.
No, it don't have anything. I manually entered my details.

Anyway the problem is not over :( I've done the above things but it is  not working..

==
BTW, I've tried **sudo /etc/init.d/networking restart** to see the problem and I got one error. Result:

[IMG]http://img264.imageshack.us/img264/9168/screenshotubuntu.png[/IMG]

I've also tried **/usr/local/bin/crclient -u rams** in Terminal and got same error .**/crclient: You can run the executable with name 'crclient' only.**

What's the problem guys?

---

### Post by kpkeerthi on 2009-04-16
Post the contents of /etc/network/interfaces

---

### Post by Alekz_ on 2009-04-16
I don't know the app crclient, but I think that ONLY the crclint file doesn't work...

Whats the content of the directory you used to run the script (/home/your_username/Desktop/crclient/)? Maybe there are some files needed by the application.. 

POst here the content and we'll see! :)

Oww! Post the content of the /etc/network/interfaces too!

---

### Post by rams123 on 2009-04-16
Contents of /etc/network/interfaces :

When I first opened it, I've seen some thing like auto lo eth0 in it. I'd deleted that and entered below settings.

```
iface eth0 inet static
            address 192.168.2.224
            netmask 255.255.255.0
            gateway 192.168.2.1
            up /usr/local/bin/crclient -u rams

auto eth0
```

I've attached crclient folder. (It's in zip, if you extract that you'll get crclient folder)

---

### Post by rams123 on 2009-04-17
Bump :(

I guess every thing is going correct. The only problem I can see is that command(**up /usr/local/bin/crclient -u rams**) is not working..

Does anyone have an idea?

---

### Post by percypais on 2011-04-30
I solved this problem with the cyberoam client by using the following shell files.

Note: I've kept the login client in the /opt/cyberoam/crclient/ directory. You can keep it wherever you please.

login.sh
```

#!/bin/sh
cd /opt/cyberoam/crclient/
./crclient -u <USERNAME>
```logout.sh
```
#!/bin/sh
cd /opt/cyberoam/crclient/
./crclient -l
```

---

