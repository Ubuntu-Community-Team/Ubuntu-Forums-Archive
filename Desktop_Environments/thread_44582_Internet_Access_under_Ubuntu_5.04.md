---
title: "Internet Access under Ubuntu 5.04"
date: 2005-06-26
forum: Desktop Environments
---

### Post by Jokerman on 2005-06-26
Loaded Ubuntu 5.05 over the weekend and having two problems.

The major one is that I can't connect to the internet using an external 56k dial up modem.

I've opened the Moden Connection via Admin -> Networking, entered the phone no., username and passwd under General; autodetected the modem on com1 under Modem and set it as the default under Options. Then I select the modem and click activate. The moving bar with ppp0 comes up and sits there for a long time without the modem dialling and yes the modem has worked with a Windows PC. Eventually an error comes back saying cannot connect.

Any clues or suggestions greatfully received.

---

### Post by Digitallysick on 2005-06-26
Are you sure you dont have a 'win" modem, What brand internal modem do you have?

---

### Post by Jokerman on 2005-06-26
As mentioned in my initial msg it is an external modem not internal. In fact that is why I went for the external modem in the first because of the very issue u raise.

---

### Post by llamakc on 2005-06-27
Now tell us what modem you have and lets see what kernel modules you have loaded. Also, how about them logs?

---

### Post by stubby on 2005-06-27
I recently formatted and had to go through a fews hoops myself to get the modem up and running.

I too have an external modem.

What i had to do was set up wvdial. This program is command line based app that let's you dial out.

```
sudo wvdialconf /etc/wvdial.conf
``` 

This will create a configuration file for you by detecting which modem you have and where it is installed. It'll also create the necessary dummy login and password entries you need to dial into your ISP.

You'll need to edit the file manually to specify those entries to suit your need, so

```
sudo gedit /etc/wvdial.conf
``` 

Enter the required telephone number, login, password. Also, remove the leading ; at the beginning of each entry. No idea why they're there.. but it won't work if it's left there. 

Finally, to test it all, type

```
sudo wvdial
``` 

And that should work. For now, let's try all that first and see how you go. If you want a gui frontend then it's just simply

```
sudo apt-get install gnome-ppp
```

EDIT: Stuff the ppp0 dialer that's in System->Networking... never worked for me either. Make sure it's set to "not configured" when you try the above solution.

---

### Post by Jokerman on 2005-06-30
To IIamakc,

Not sure how the name of the modem will help but here it is - a Dynalink 1456VQ.

Hope that helps.  

I followed the directions of Stubby and now I'm on the net and am replying from home under Ubuntu. Thanks for your email.

---

### Post by Jokerman on 2005-06-30
[QUOTE=stubby]I recently formatted and had to go through a fews hoops myself to get the modem up and running.

I too have an external modem.

What i had to do was set up wvdial. This program is command line based app that let's you dial out.

```
sudo wvdialconf /etc/wvdial.conf
``` 

This will create a configuration file for you by detecting which modem you have and where it is installed. It'll also create the necessary dummy login and password entries you need to dial into your ISP.

You'll need to edit the file manually to specify those entries to suit your need, so

```
sudo gedit /etc/wvdial.conf
``` 

Enter the required telephone number, login, password. Also, remove the leading ; at the beginning of each entry. No idea why they're there.. but it won't work if it's left there. 

Finally, to test it all, type

```
sudo wvdial
``` 

And that should work. For now, let's try all that first and see how you go. If you want a gui frontend then it's just simply

```
sudo apt-get install gnome-ppp
```

EDIT: Stuff the ppp0 dialer that's in System->Networking... never worked for me either. Make sure it's set to "not configured" when you try the above solution.[/QUOTE]
 Thanks Stubby the details u gave were just what the doctor ordered and  I'm up and running....

---

