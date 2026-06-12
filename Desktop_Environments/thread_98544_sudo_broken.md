---
title: "sudo broken?"
date: 2005-12-03
forum: Desktop Environments
---

### Post by BrianB on 2005-12-03
Hi, I cant use any admin apps (Synaptic etc.) at all. When I try to run them I just get nothing. I also can't use sudo via the terminal, I get "unable to look up ubuntu via gethostname ()". Also after login I get the message "Could not look up internet address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts"? So I just click log in anyway. Anybody know what's up?

---

### Post by 23meg on 2005-12-03
You probably accidentally deleted your default hosts config. Please post the contents of your /etc/hosts file.

---

### Post by MighMoS on 2005-12-03
I also have this problem.  But I just installed.  I can run the apps once, and then it asks me for my password.  I enter it and the dialog box goes away.  After trying to open up another admin app, nothing happens.

Does this sound like the same problem?

EDIT: Guess I should have searched just a little harder.  I su'ed into root, and ran "visudo".  Added my name to the end of the file, with the same things as root and it works now.

---

### Post by 23meg on 2005-12-03
Not sure, it might be a similar problem with hosts. It won't hurt if you post your /etc/hosts file as well.

---

### Post by BrianB on 2005-12-03
Tis is my /etc/hosts ```
127.0.0.1 localhost
``` but this was a fresh install so I couldn't have deleted anything accidentally. > Does this sound like the same problem? Sort of but I couldn't ever run the apps.

---

### Post by 23meg on 2005-12-03
It indeed seems you have deleted some things accidentally. Edit your /etc/hosts to look like this```
127.0.0.1 localhost.localdomain localhost YOURMACHINENAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```obviously replacing YOURMACHINENAME with the name you chose for your computer at installation.

---

### Post by Manojo on 2005-12-03
Hi, sorry to barge in .. got the same problem..

Tried modifying through gedit, but unable to type anything (I guess it is root protected.. am I right?) what to do ?

Thanks,
Manojo

---

### Post by 23meg on 2005-12-03
[QUOTE=Manojo]Hi, sorry to barge in .. got the same problem..

Tried modifying through gedit, but unable to type anything (I guess it is root protected.. am I right?) what to do ?

Thanks,
Manojo[/QUOTE]```
sudo gedit /etc/hosts
```will do it.

Btw, you can find the name you gave to your machine with the command ```
hostname
```

---

### Post by Manojo on 2005-12-03
the sudo command at my place doesn't work.. I get the following message :

> unable to lookup manojo via gethostbyname()

It's a new install for me too, and I did not configure my network during install.. Could that be a problem ?

by the way, hostname returns manojo

Thanks,
Manojo

---

### Post by 23meg on 2005-12-03
Try my instructions in post #6.

---

### Post by tukuyomi on 2005-12-03
[QUOTE=23meg]Try my instructions in post #6.[/QUOTE]
I think he needs sudo and his root passwd to edit /etc/hostname
I guess you need to boot with your install CD with the 'rescue' mode...

---

### Post by Manojo on 2005-12-03
I'm sorry, but I don't think I get it.. you mean to say I've got to check post #6 of this thread ?

I just posted I couldn't type a thing in my hosts file.. I'm totally confused :S

Manojo

---

### Post by 23meg on 2005-12-03
Oops, forgot it, tukuyomi is right. If you can't use sudo, you'll need to boot into recovery mode and edit your /etc/hosts file to look the way I described in post #6. You can do this with ```
sudo nano /etc/hosts
```

---

### Post by invalid on 2005-12-03
[QUOTE=23meg]Oops, forgot it, tukuyomi is right. If you can't use sudo, you'll need to boot into recovery mode and edit your /etc/hosts file to look the way I described in post #6. You can do this with ```
sudo nano /etc/hosts
```[/QUOTE]

From the past posts, with the same problem, recovery mode results in the same situation. 

The only times I remember this problem being fixed, is using a recovery cd like Knoppix to edit the file. Afterwards, you should be good to go.

Cheers,
Cb

---

### Post by tukuyomi on 2005-12-03
I think the 'rescue' mode allows you to use a root shell... going to test right now ;)

---

### Post by BrianB on 2005-12-03
su to root and then you should be able to edit the file with gedit /etc/hosts.

---

### Post by Manojo on 2005-12-03
[QUOTE=23meg]Oops, forgot it, tukuyomi is right. If you can't use sudo, you'll need to boot into recovery mode and edit your /etc/hosts file to look the way I described in post #6. You can do this with ```
sudo nano /etc/hosts
```[/QUOTE]
I'm lucky recovery method worked for me.. thanks a lot 23meg :-). But a question though.. what exactly did I do ? Would like to understand in order to start it the right way with linux :-)

Thanks,Manojo

---

### Post by 23meg on 2005-12-03
The /etc/hosts file maps IP adresses to hostnames and aliases. If you don't have the first line that will map the IP adress of localhost (being a fixed 127.0.0.1 in all systems) to your main local host, which is your machine, you lose the ability to perform administrative commands because you lose all network awareness.```
man hosts
``` will give you more info.

---

### Post by Brent Dax on 2005-12-03
(Deleted--sorry, didn't see second page of thread.)

---

### Post by 23meg on 2005-12-03
Did you read the rest of the thread? He doesn't need to boot with the live cd, the recovery mode will do. It's best to resort to live cd solutions only when recovery mode is borked as well (which is really rare).

---

### Post by BrianB on 2005-12-04
How did you get it fixed? I did what it said in post #6 and now I got rid of the message after login but I still can't run anything admin by just clicking on it.

---

### Post by Manojo on 2005-12-04
Well, I dit what was in post #6, and to do that I started Ubuntu under recovery mode, and edited the file through
nano /etc/hosts (as you might have done too)
Then I just rebooted normal and the message disappeared.. I performed a few tests under the Terminal(such as mounting my Windows partition),  and it worked just fine.

As for using the GUI, I was able to update and install VLC without a problem.. Of course it asked me for my root password, but that's all..

Curious it doesn't work for you :S

Manojo

---

### Post by BrianB on 2005-12-04
Anybody know whats wrong?

---

### Post by tukuyomi on 2005-12-04
Can you post your /etc/hosts file here, please?
Btw, just to be sure, did you actually save the file after editing? (nano --> CTRL+X, then Y -to save- and ENTER -to confirm the filename-)?

---

### Post by BrianB on 2005-12-04
It's identical to the one 23meg posted and yes I did save it.

---

### Post by BLTicklemonster on 2006-02-09
BrianB, I just upgraded to dapper and have had numerous problems (hint, don't upgrade until it is totally beta, which isn't now). One of them is that I can't use sudo and have the same problems posted here.

I am about to go and boot into recovery mode and log in with my username and password or whatever it asks me (I was just there, but don't remember, but actually I think it stops and asks if you want to put in your password to do maintenance, at which point you put in your password), then at the dollar sign, I'm going to put 

```
nano /etc/hosts
```

(no need to put sudo, besides, I can't use sudo!)

and enter this:

127.0.0.1 localhost.localdomain localhost YOURMACHINENAME

and ctrl+o, press enter, then press ctrl+x and reboot and see what happens.


*edit: BINGO, it worked. The reason I just had to do that, Im sure, is because I followed advice elsewhere that said to make that particular line read:

0.0.0.0 localhost

as part of stopping advertisements and pop ups.

So try that and see if it works for you.

---

