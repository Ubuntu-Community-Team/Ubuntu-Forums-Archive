---
title: "Nautilus root help?"
date: 2009-03-07
forum: General Help
---

### Post by coldmack on 2009-03-07
Hello, I am trying to use nautilus under the root permission, but it is not working for me. I hit alt F2 and then type in gksudo nautilus, which it then asks for a password. I type the password in, but nothing happens. When I try it again nothing happens at all. Any ideas on why this is occurring and how I can get nautilus running as root? I am running the MIE version, which is ubuntu 8.04 on my HP. Thank you.

---

### Post by taurus on 2009-03-07
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```
What happens when you run this command?

```
sudo apt-get update
```
When you type in your password, you won't see the cursor move so make sure you type it right and hit Return.

---

### Post by LoneWolfJack on 2009-03-07
have the same problem... in fact, the "run" window doesn't work at all for me no matter what I enter there... just run the same command from a terminal window.

---

### Post by thtrgremlin on 2009-03-07
I don't like the run box either because you miss any and all useful output. Sucks that it isn't working like it is supposed to though.

---

### Post by mike555 on 2009-03-07
When you type in your password in terminal it isn't suppose to show (security measure) but it is going in .....

---

### Post by Tews on 2009-03-07
I had this problem and solved it like this ... System>Preferences>Sessions . click on Startup Programs, and click on ADD ... Name it something like Root .. in the command line enter .. gksudo nautilus .. and there you have it .. when you start the launcher you will have nautilus running as root! :D

---

### Post by coldmack on 2009-03-09
I try it out when I get the chance thank you.

---

### Post by Tony Flury on 2009-03-09
Having Nautilus starting up as root as a default Application each time you log in, is not a good idea in my opinion, as in one step you have just circumvented the vast majority of Linux's protection mechanisms.

It would be far better to solve the problem where by you run a Sudo Nautilus session when you need it - which should be few and far between.

---

### Post by coldmack on 2009-03-09
Well I tried it, and it did promt me for my passowrd, but alas I still did not have root access in nautilus. Any other suggestions?

---

### Post by Tews on 2009-03-09
> **coldmack said:**
> Well I tried it, and it did promt me for my passowrd, but alas I still did not have root access in nautilus. Any other suggestions?

I rechecked just to be sure and it works perfectly .. When you enter your password, does Nautilus open??  Double check the command line ... Let me know what happens ... :)

---

### Post by stanz on 2009-03-09
new icon on panal...

**name:** whatever
**command:** gksu nautilus

click it when ya need it...

---

### Post by mªrty on 2009-03-09
> have the same problem... in fact, the "run" window doesn't work at all for me no matter what I enter there... just run the same command from a terminal window. 
When you press Alt-F2, make sure "Run in Terminal" is checked before you hit Enter.

---

### Post by coldmack on 2009-03-09
> **Tews said:**
> I rechecked just to be sure and it works perfectly .. When you enter your password, does Nautilus open??  Double check the command line ... Let me know what happens ... :)
No, it did not even open. I double checked and stuff but nothing at all. Could be the fact that I am running the MIE linux HP gave?

> **stanz said:**
> new icon on panal...

**name:** whatever
**command:** gksu nautilus

click it when ya need it...

How do I do that? As stated I am on MIE version of ubuntu which came as the default os on my netbook/umpc.

---

### Post by coldmack on 2009-03-09
So I decided to run it as terminal to see what happens. Still nothing. But this what it says in terminal after the password was typed in, after terminal closes nothing else happens.

---

### Post by taurus on 2009-03-09
Post your /etc/hostname & /etc/hosts.

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by scphan on 2009-03-09
does it work when you enter 'sudo nautilus' in the terminal?

---

### Post by coldmack on 2009-03-09
Sounds like someone wants my ip and open ports and such if i post wants in hosts. 

If I type in sudo nautilis I get this.
sudo: unable to resolve host alex-umpc
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault

---

### Post by taurus on 2009-03-09
> **coldmack said:**
> **[COLOR="Red"]Sounds like someone wants my ip and open ports and such if i post wants in hosts.[/COLOR]** 

If I type in sudo nautilis I get this.
sudo: unable to resolve host alex-umpc
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault

](*,)

Do you even know what you have just said?  How am I going to get your IP or open ports with the outputs of those two commands?

If you don't feel comfortable of posting a command (or commands), then don't.

---

### Post by coldmack on 2009-03-09
alright here is what is states

# Generated by Moblin Image Creator #
127.0.1.1 localhost localhost.localdomain ume al-umpc.State network

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback

---

### Post by stanz on 2009-03-10
> **coldmack said:**
> So I decided to run it as terminal to see what happens. Still nothing. But this what it says in terminal after the password was typed in, after terminal closes nothing else happens.
If I type in sudo nautilis I get this.
sudo: **unable to resolve host alex-umpc**
**seahorse nautilus** module initialized
**Initializing [COLOR=DarkRed]nautilus-share[/COLOR] extension**

Why is it wanting to access the web?
Why is it looking at 'sudo' as a web addy?
or to 'share'?.... and the extension?
This don't sound right...kinda looks like its doing a dns lookup...why? 
The nautilus-share...is this your doing for home or work?

If you have no options in nautilus for 'Open as Administrator' or 'Run as Root', open synaptic package manager or whatever ya got, and search for
'Nautilus actions configurations' {or the like} ..you already have the share extension.

Whatever flavor of Ubuntu you have - you have a panel, and an option to add icons to that panel..(aka: Application Launcher).thats what I'm talking about- adding a root nautilus to your panel...or desktop--a short cut..a custom application launcher.

---

### Post by stanz on 2009-03-10
> **taurus said:**
> ](*,)

Do you even know what you have just said?  How am I going to get your IP or open ports with the outputs of those two commands?

If you don't feel comfortable of posting a command (or commands), then don't.

This is pretty harmless...we're just trying to help ya, but need to understand whats going on here first!  :)

---

### Post by coldmack on 2009-03-10
i try that suggestion thank you.

---

### Post by coldmack on 2009-03-11
Anyone other ideas? I installed what was suggested but not sure what to do next.

---

