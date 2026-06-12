---
title: "Device name"
date: 2024-11-28
forum: Desktop Environments
---

### Post by AnupamMitra on 2024-11-28
Few days back I have installed Ubuntu 24.04.1 in one of my PCs. Now-a-days when I open the Terminal it is found that the device name is shown twice, as under. 
nareesh-pal-memorial-trust@nareesh-pal-memorial-trust-H310M-S2-2-0:~$
This was not the position earlier. Now I would like to rectify it. How it is to be rectified? Kindly advise.

---

### Post by grahammechanical on 2024-11-28
What you are seeing is username@computername.

The install process asks us for our name; the device/computer name and then our user name. When I enter my full name (Christian + Surname) the installer assumes that to be the user name and puts a hyphen between my two names. I edit the user name to something more useful. If I do not notice this "helpful" action my user name would be Christian name-Surname. This has happened with one install that I put in.

I think that is what has happen here. 

Regards

---

### Post by Dennis N on 2024-11-28
> ...Now I would like to rectify it. How it is to be rectified? Kindly advise. 
Edit Device Name by going to: 
Settings > System > About
Edit User Name by going to:
Settings > System > Users

---

### Post by ActionParsnip on 2024-11-28
What is the output of
```

echo "username - `whoami`"; echo "hostname - `hostname`"

```

---

### Post by AnupamMitra on 2024-12-05
> **grahammechanical said:**
> What you are seeing is username@computername.

The install process asks us for our name; the device/computer name and then our user name. When I enter my full name (Christian + Surname) the installer assumes that to be the user name and puts a hyphen between my two names. I edit the user name to something more useful. If I do not notice this "helpful" action my user name would be Christian name-Surname. This has happened with one install that I put in.

I think that is what has happen here. 

Regards

Thanks for your cooperation. I have rectified it through Settings > System > About. 

Regards.

---

### Post by AnupamMitra on 2024-12-05
> **Dennis N said:**
> Edit Device Name by going to: 
Settings > System > About
Edit User Name by going to:
Settings > System > Users

Thanks for your reply. It stands rectified as per your suggestions. 

Regards.

---

### Post by AnupamMitra on 2024-12-05
> **ActionParsnip said:**
> What is the output of
```

echo "username - `whoami`"; echo "hostname - `hostname`"

```

Thanks for your support. Now it stands rectified through Settings > System > About. 

Regards.

---

### Post by oldfred on 2024-12-05
I always make my username fred and use hardware version plus install name for hostname. I have several systems and in each may have multiple installs, so need to keep track of which is which.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo "username - `whoami`"; echo "hostname - `hostname`" [/COLOR]
username - fred 
hostname - z170-noble
[/FONT]
```

---

