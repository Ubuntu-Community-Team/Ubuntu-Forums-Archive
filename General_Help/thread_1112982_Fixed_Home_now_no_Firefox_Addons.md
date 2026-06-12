---
title: "Fixed Home now no Firefox Addons"
date: 2009-04-01
forum: General Help
---

### Post by kehon on 2009-04-01
I just fixed my home directory and permissions and now firefox addons are disabled or whatever when i check addons they arent disabled and they are listed but they arent working / present

---

### Post by pmlxuser on 2009-04-01
Why don't you just reinstall the addons , easiest if you have a good internet connection..

---

### Post by kehon on 2009-04-01
have to many addons and no good internet connection very slow and weak at colledge

---

### Post by coffeecat on 2009-04-01
> **kehon said:**
> I just fixed my home directory and permissions

What exactly did you do? The firefox addons and configurations are in your home folder in the hidden ~/.mozilla folder. Perhaps there is still a premissions problem somewhere in ~/.mozilla. The actual addons are in ~/.mozilla/firefox/*randomstring*.default/

---

### Post by kehon on 2009-04-01
to be truthfull i dont remember i moved the home directory to /home/kurt/home by accident from and ntfs partition then booted into recovery root shell and got it to move home to /home/home then deleted kurt and moved/renamed(mv) /home/home to /home/kurt and did usermod -d kurt /home/kurt and chown kurt; chmod -R 700 /home/kurt; chmod 644 /home/kurt/.dmrc and it started up with no errors and wine worked again and thats about it

---

### Post by coffeecat on 2009-04-01
You didn't do a recursive chown, so I should imagine some of the folders and files in home have not been reset. Try:

```
sudo chown kurt: -R ~/
```I'm suggesting that you use sudo, because I can't quite follow what happened to the contents of your home folder, and if some of the permissions are wrong it's possible you'll need admin privileges to do the chown.

---

### Post by kehon on 2009-04-01
cool thanks that worked but i also enabled and disabled all of them restarted and then reenabled so i dont know which worked but thanks

---

