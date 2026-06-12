---
title: "Custom Boot - Autologin &amp; Run User App (no X)"
date: 2009-04-29
forum: General Help
---

### Post by chrisp_bbcrd on 2009-04-29
I'm fairly new to Linux and I've been developing an application in Qt/Embedded to run on a [Viglen MPC-L]("http://www.viglen.co.uk/viglen/Products_Services/Product_Range/Product_file.aspx?eCode=XUBUMPCL&Type_Info=Description&Type=Desktops") with an AMD Geode GX2 400MHz processor. These things come installed with xubuntu 7.04.

I want to configure the boot options so that it boots up and automatically logs in as root without starting X. Then launches my bash script which sets the required environment variables and runs the Qt/Embedded app, using an infinite loop to restart the app if it exits.

Since these things are so slow I need to reduce the number of other processes running as much as possible. First off, is xubuntu suitable rather than ubuntu server edition for example? And if it is, can someone please give me some advice on the steps I need to take to get this to happen. I've been a bit overwhelmed trying to find what i need in existing threads.

Thanks,
Chris

---

### Post by chrisp_bbcrd on 2009-04-29
Just to note: The PCs won't be networked, this is their sole use so security isn't really an issue.

---

### Post by chrisp_bbcrd on 2009-04-30
Update:
Here's what I've done so far. Someone tell me if I'm way off the mark.

- Created /etc/inittab and set the default runlevel to 3.
- Added my script to /etc/init.d/ and ran rc-update.d to create a symbolic link in /etc/rc3.d/ pointing to the script. I set the sequence number to 99 so everything else is done first.
- I renamed any links Snnproc_name to processes that I thought weren't needed in /etc/rc.d/ to start with Kmmproc_name where mm=100-nn. Including gdm.

Everything's fine except if I close the application it doesn't reopen, it goes to the console login instead. The loop in my bash script is below, fairly simple. Is an infinite loop just ignored in an init script?
```

while[1]
do
   exec my_process
done

```

---

