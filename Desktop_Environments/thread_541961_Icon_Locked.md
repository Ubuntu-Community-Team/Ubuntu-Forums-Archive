---
title: "Icon Locked"
date: 2007-09-03
forum: Desktop Environments
---

### Post by kcid2829 on 2007-09-03
I have a cnijfilter for a Canon printer on my desktop, which I can't remove.  When I try to, I get a message that I don't have permissions to change it or it's parent folder.  It has a padlock Icon showing.  It got there when I unzipped a file, and then used Alien 8.65 to convert it to a deb file.  Then when I ran that deb file, it shoed a few filter files.  I got rid of the others.  Can anyone tell me how to get rid of this from the desktop?  Thanks in advance.

---

### Post by taurus on 2007-09-03
Remove it from a terminal with sudo command

Applications -> Accessories -> Terminal
```
sudo rm filename
```
or use nautilus with root privilege.
```
gksudo nautilus
```

---

### Post by kcid2829 on 2007-09-03
Neither the terminal method nor the nautilus method would remove it.  Any other suggestions anyone?

---

### Post by taurus on 2007-09-03
Where are those files (exact path) and what are the names of them?

---

### Post by kcid2829 on 2007-09-03
The icon is on my desktop.

---

### Post by taurus on 2007-09-03
What's the output of this command from a terminal then?

```
ls -la ~/Desktop
```

---

### Post by kcid2829 on 2007-09-03
Thanks for your help, Taurus.   I'm kind of a newbie.  The terminal command you asked about results in:
drwxr-xr-x 4 root root 4896 2007-8-26 10:35 cnujfilter-common-2.60.I guess these are atributes, dates, and?  Can you suggest further?

---

### Post by taurus on 2007-09-03
Do you want to remove that directory, cnujfilter-common-2.60?  Or do you only want to remove stuff in it?

---

### Post by kcid2829 on 2007-09-03
I mainly want to get it off the Desktop.  I'd like to completely remove it if it wouldn't mess up my turboprint printer setup.

---

### Post by taurus on 2007-09-03
You can remove it from your machine if you have installed a driver for your printer with it.  Have you done anything with it after you unpacked it?

---

### Post by kcid2829 on 2007-09-04
I can't do anything with it, including moving it to another folder, because it says I don't have permissions.  When I click it, I get a window showing a debian folder and a usr folder, and those have various files in them.  My printer is set up thru Turboprint(the free version).

---

### Post by kcid2829 on 2007-09-04
After I do the ls -la, etc in nautilus,  I get the listings.  But then what do I do to get rid of the file on the Desktop.  I noted that you, taurus had helped another person with the identical problem.  That person was able to delete the file, then.  What are the next steps?  Thanx.

---

### Post by taurus on 2007-09-04
> **kcid2829 said:**
> After I do the ls -la, etc in nautilus,  I get the listings.  But then what do I do to get rid of the file on the Desktop.  **I noted that you, taurus** had helped another person with the identical problem.  That person was able to delete the file, then.  What are the next steps?  Thanx.

Oh me!  :oops:

So, you want to remove that directory, cnujfilter-common-2.60, off your computer?

```
cd ~/Desktop
sudo rm -rf cnujfilter-common-2.60
ls -la
```

---

### Post by kcid2829 on 2007-09-05
Thanks loads, Taurus.  That last command did it.  I've printed out the complete help manual, but have a lot more reading to do, and this forum is really very helpful.

---

