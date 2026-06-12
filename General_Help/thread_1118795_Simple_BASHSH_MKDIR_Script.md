---
title: "Simple BASH/SH MKDIR Script"
date: 2009-04-07
forum: General Help
---

### Post by Aysah on 2009-04-07
Normally I would just take the time to figure this out but I'm kind of running out of time here.  We have a whole slew of customers who just recently are being transitioned to a different folder hierarchy on our server and each customer has to be transitioned one by one.

I need a script that will just ask me for the customers name and store it in a variable called "cname".  At that point, the script will make the following directories dynamically with the appropriate ownerships and permissions:

/home/[cname] (root:[cname], 755)
/home/[cname]/FROM ([cname]:ezlinksystem, 770)
/home/[cname]/TO ([cname]:ezlinksystem, 770)
/IN.Archive/[cname] (root:[cname], 755)
/IN.DataFiles/[cname] (root:ezlinksystem,  770)
/OUT.Archive/[cname] (root:[csname], 755)
/OUT.DataFiles/[cname] (root:ezlinksystem,  770)

---

### Post by scragar on 2009-04-07
```
while [ true ]; do
  read cname;
  mkdir -m 755 -p "/home/$cname";
  mkdir -m 770 -p "/home/$cname/FROM";
  mkdir -m 770 -p "/home/$cname/TO";


  chown -R root:$cname /home/$cname;
  chown $cname:ezlinksystem /home/$cname/*;
  
done;
```You can figure out the last 4, right?

---

### Post by ibuclaw on 2009-04-07
Is this creating new accounts for people, or creating new directories and setting up the accounts later?

Anyhow: **read** will accept an input, and **mkdir** will create a directory, and **chown** will set ownership.

This is the rudimentary jist of what you are looking for.
May need it in a while loop to speed things up.
```
read -p "Enter Customer Name: " cname

mkdir -m755 /home/$cname
mkdir -m770 /home/$cname/FROM
mkdir -m770 /home/$cname/TO
mkdir -m755 /IN.Archive/$cname
mkdir -m755 /OUT.Archive/$cname
mkdir -m770 /IN.DataFiles/$cname
mkdir -m770 /OUT.DataFiles/$cname

chown root:$cname /home/$cname
chown $cname:ezlinksystem /home/$cname/*
chown root:$cname /IN.Archive/$cname
chown root:$cname /OUT.Archive/$cname
chown root:ezlinksystem /IN.Datafile/$cname
chown root:ezlinksystem /OUT.Datafile/$cname

```
Simple really.

Regards
Iain

---

### Post by Aysah on 2009-04-07
> **tinivole said:**
> Is this creating new accounts for people, or creating new directories and setting up the accounts later?

Regards
Iain

Thanks again for all your help, I appreciate it VERY much.  This script is for both technically.  We have a new server that we just threw together.  I knew how to make the beginning part of the script with adding new users so I thought I would only ask for the part I didnt quite understand.

Hopefully I'm not asking too much but I was hoping if you could help me with one last part.  A condition.  The users can be what we consider two different types (ctg-a and ctg-b)  I guess what i want to do is after asking for customer name, I want to ask what category they are in and make a directory based off of that.

ctg-a: /etc/IN.tbs.ctga
ctg-b: /etc/IN.tbs.ctgb


Thanks again for all your time.  :-)

---

