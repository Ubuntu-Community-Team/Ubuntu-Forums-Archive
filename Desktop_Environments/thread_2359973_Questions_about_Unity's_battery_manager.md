---
title: "Questions about Unity's battery manager"
date: 2017-04-30
forum: Desktop Environments
---

### Post by rrdnt on 2017-04-30
A very newbie question. My desktop environment right now is Unity (Ubuntu 16.04 LTS). I find when the battery is running low, a warming will pop up with message such as battery critical. I quite like this feature, so a few questions. 

What's the name of this battery manager? 
Which command can I use to configure or launch it? (I know I can configure through system settings' power but I want to use this app in other environment where there is no Unity like UI to click system settings, etc.)


Or any place there contains related doc? Searching with keywords like 'ubuntu unity battery manager' doesn't find the name, etc. information. 

Thanks

---

### Post by Autodave on 2017-04-30
Not quite sure what you are trying to do or ask. The power manager is on all Ububtu flavors: Xubuntu, Lubuntu, etc. If NOT in stalled, simply go to the software center or synaptic and search and install.

---

### Post by rrdnt on 2017-04-30
> **Autodave said:**
> Not quite sure what you are trying to do or ask. The power manager is on all Ububtu flavors: Xubuntu, Lubuntu, etc. If NOT in stalled, simply go to the software center or synaptic and search and install.
   
Right now  my Unity desktop environment already has battery manager installed. But I may want to use it in other environment. But I do not know the name of package. For instance when executing `apt-get install <package name of unity battery manager>` What name should I place after apt-get install command?

Thanks

---

### Post by Autodave on 2017-04-30
On Xubuntu (which I am using) you would right click on top banner and then Panel and then  ADD New. From the drop down list, choose Power Manager Plugin.

Is that what you are looking for?

---

### Post by Frogs Hair on 2017-04-30
What other environment ?

```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by rrdnt on 2017-05-01
> **Autodave said:**
> Not quite sure what you are trying to do or ask. The power manager is on all Ububtu flavors: Xubuntu, Lubuntu, etc. If NOT in stalled, simply go to the software center or synaptic and search and install.

What (power manager's) name should I use when installing power manager in terminal? e.g. apt-get install <power manager> 

My problem is I don't know the name. Thanks

---

### Post by rrdnt on 2017-05-01
> **Autodave said:**
> On Xubuntu (which I am using) you would right click on top banner and then Panel and then  ADD New. From the drop down list, choose Power Manager Plugin.

Is that what you are looking for?

No. I am looking for the name/ package name of power manager used by Unity desktop. Thanks.

---

### Post by rrdnt on 2017-05-01
> **Frogs Hair said:**
> What other environment ?

```
echo $XDG_CURRENT_DESKTOP
```

  
Executing the command returns **Unity**.

---

### Post by Autodave on 2017-05-01
Go into SYNAPTIC and search for POWER MANAGER.

---

### Post by Frogs Hair on 2017-05-02
> Right now  my Unity desktop environment already has battery manager installed. _But I may want to use it in other environment_.

You wrote you could access the power manager in Unity , but I was trying to find out what the other environment was.

---

### Post by rrdnt on 2017-05-02
> **Frogs Hair said:**
> You wrote you could access the power manager in Unity , but I was trying to find out what the other environment was.

I want to use it in i3-wm. Previously I used i3 but I found there is no, e.g., alarming when battery falls below a particular threshold.

---

### Post by Frogs Hair on 2017-05-02
Some use the xfce4 power manager, but the methods to get it working  in i3 vary based on a web search.

---

### Post by rrdnt on 2017-05-02
> **Autodave said:**
> Go into SYNAPTIC and search for POWER MANAGER.

After installing synaptic, I notice gnome-power-manager is the only power manager tool installed (`apt-get install gnome-power-manager` shows it's installed already); however, I check with command `ps -ef | grep gnome-power` or `ps -ef | grep gnome | grep power`  doesn't find any process related gnome power manager as suggested by gnome manual. 

[https://help.gnome.org/users/gnome-power-manager/stable/using.html.en](https://help.gnome.org/users/gnome-power-manager/stable/using.html.en) 

How do I find which power manager is running or used by Unity? Thanks

---

### Post by Frogs Hair on 2017-05-02
> **rrdnt said:**
> After installing synaptic, I notice gnome-power-manager is the only power manager tool installed (`apt-get install gnome-power-manager` shows it's installed already); however, I check with command `ps -ef | grep gnome-power` or `ps -ef | grep gnome | grep power`  doesn't find any process related gnome power manager as suggested by gnome manual. 

[https://help.gnome.org/users/gnome-power-manager/stable/using.html.en](https://help.gnome.org/users/gnome-power-manager/stable/using.html.en) 

How do I find which power manager is running or used by Unity? Thanks


Unity uses the gnome power manager, but it has modifications to suit Ubuntu.

---

### Post by rrdnt on 2017-05-03
> **Frogs Hair said:**
> Unity uses the gnome power manager, but it has modifications to suit Ubuntu.

So which command can I use to launch the setting of (ubuntu version) gnome power manager? I want to configure it.
And what command can I use to start/ execute gnome power manager other than Unity desktop environment?

Thank you for your kindly help.

---

### Post by Frogs Hair on 2017-05-03
It would have to be added to the i3 window manager configuration and I have no information on how to go about that . As posted earlier some users have configured the xfce4 power manger to work with i3 , but you would have to research how it was done. I did get some hits in my search.

---

