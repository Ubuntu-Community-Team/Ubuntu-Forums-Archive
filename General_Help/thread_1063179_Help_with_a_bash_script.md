---
title: "Help with a bash script"
date: 2009-02-07
forum: General Help
---

### Post by mykrob on 2009-02-07
I am running Ubuntu 8.10, and as some of you may have noticed, USB transfer can be a bit slow, to say the least. I found in the forum that unloading a couple of modules then reloading them in the "correct" order makes USB transfer run a lot faster.
I have tested this several times by removing them manually, then reloading them.

I want to make a script that will do this for me and put it in my autorun directory, but am not sure how.

The commands i need to run are as follows:
```

sudo rmood ehci_hcd
sudo rmmod uhci_hcd
sudo modprobe ehci_hcd
sudo modprobe uhci_hcd

```

In that order.

How can I make a bash script that will automatically run this at startup without asking for the password?

Thanks,
-myk

---

### Post by x22 on 2009-02-07
not hard: give yourself root authority "passwd root"
then forget the "sudo"s

---

### Post by terry_gardener on 2009-02-07
i have attached the bash script that should do the job. 
first download it somewhere. 
make it executable. 
and then install schedule task program 

sudo apt-get install gnome-schedule

open this with root permissions and then add the script to be ran on every reboot. 

to open with root permissions "gksu /usr/bin/gnome-schedule"

this should run the script every time you boot up using the root users privileges. 

hope this helps 

sadly i have not tried this myself so let me know how you get on.

---

### Post by dcstar on 2009-02-07
> **mykrob said:**
> I am running Ubuntu 8.10, and as some of you may have noticed, USB transfer can be a bit slow, to say the least. I found in the forum that unloading a couple of modules then reloading them in the "correct" order makes USB transfer run a lot faster.
I have tested this several times by removing them manually, then reloading them.

I want to make a script that will do this for me and put it in my autorun directory, but am not sure how.

The commands i need to run are as follows:
```

sudo rmood ehci_hcd
sudo rmmod uhci_hcd
sudo modprobe ehci_hcd
sudo modprobe uhci_hcd

```

In that order.

How can I make a bash script that will automatically run this at startup without asking for the password?

Thanks,
-myk

Put them in /etc/rc.local (without the sudo), that is what that file is for.

---

### Post by mykrob on 2009-02-18
dcstar,

just put them verbatim, one per line like in my example?

Thanks,
-myk

---

### Post by Slim Odds on 2009-02-18
> **x22 said:**
> not hard: give yourself root authority "passwd root"
then forget the "sudo"s

Horrible idea.... don't do it....

Do you get asked for passwords for all the startup scripts when Ubuntu boots?

I didn't think so....

---

### Post by Slim Odds on 2009-02-18
> **mykrob said:**
> dcstar,

just put them verbatim, one per line like in my example?

Thanks,
-myk

LOL

Yes and no.... yes, just put them one per line, but change that first one to rmmod

---

### Post by mykrob on 2009-02-18
dang defective keyboard :)

Just to make sure as well, all this needs to go before exit 0, and no semicolon is needed after each line?

---

### Post by Slim Odds on 2009-02-18
> **mykrob said:**
> dang defective keyboard :)

Just to make sure as well, all this needs to go before exit 0, and no semicolon is needed after each line?

Correct....

:)

---

