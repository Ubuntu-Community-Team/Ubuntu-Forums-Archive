---
title: "ATI 5770 Triple Monitor Issue"
date: 2010-12-19
forum: Desktop Environments
---

### Post by bootsless999 on 2010-12-19
I cant seem to run my tri monitors with ubuntu 10.10. I have the driver that ubuntu recommends. I'm using 2 monitors on DVI with a 1680x1050 Resolution each, and my 3rd monitor via displayport is 1920x1080. Whenever I connect the 3rd monitor, either before boot, or on the fly, It doesn't appear in the ATI Control Center.

What can I do? Thanks.

Also, keep in mind, this is my first experience with linux (ubuntu) in a long time, so please forgive me if im missing the obvious.

Thanks again
-B

---

### Post by PhantmKllr on 2010-12-19
Just to clarify, are you using the driver installed from "System -> Administration -> Addtional Drivers", or the drivers from the ATI website?

---

### Post by bootsless999 on 2010-12-19
> **PhantmKllr said:**
> Just to clarify, are you using the driver installed from "System -> Administration -> Addtional Drivers", or the drivers from the ATI website?

The one from "System -> Admin -> Add. Drivers"

---

### Post by PhantmKllr on 2010-12-19
> **bootsless999 said:**
> The one from "System -> Admin -> Add. Drivers"
You have an ATI HD 5770?

---

### Post by bootsless999 on 2010-12-19
> **PhantmKllr said:**
> You have an ATI HD 5770?

Correct.

---

### Post by PhantmKllr on 2010-12-19
Alright. Here's the official Linux driver from the ATI website. Install it, but don't forget to remove the Ubuntu driver first. Hope this helps! :D

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

---

### Post by bootsless999 on 2010-12-19
> **PhantmKllr said:**
> Alright. Here's the official Linux driver from the ATI website. Install it, but don't forget to remove the Ubuntu driver first. Hope this helps! :D

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Alright, I removed the Ubuntu Driver, And I go to install the driver that you gave me there, and when I click on it, it says

"Could not display "/home/brandon/Downloads/ati-...ller-10-12-x86.x86_64 (1).run".The Location is not a folder"

What now? Thanks. -B

---

### Post by PhantmKllr on 2010-12-19
Alright, move the file to your Desktop, then rename it (leaving .run at the end) to something easy to remember (e.g. "ati.run"). Then go into your terminal and change directories to your desktop:

```
cd Desktop
```

Then type in:

```
sudo ati.run
```

That should work. If it doesn't, then you may have downloaded an incomplete file. Check if it's the proper size. If not, download it again. Hope that helps. :popcorn:

---

### Post by bootsless999 on 2010-12-19
> **PhantmKllr said:**
> Alright, move the file to your Desktop, then rename it (leaving .run at the end) to something easy to remember (e.g. "ati.run"). Then go into your terminal and change directories to your desktop:

```
cd Desktop
```

Then type in:

```
sudo ati.run
```

That should work. If it doesn't, then you may have downloaded an incomplete file. Check if it's the proper size. If not, download it again. Hope that helps. :popcorn:

After I do that, It says command not found when I type in sudo ati.run when after its re-named and placed on the desktop as ati.run

---

### Post by PhantmKllr on 2010-12-19
> **bootsless999 said:**
> After I do that, It says command not found when I type in sudo ati.run when after its re-named and placed on the desktop as ati.run
Try:
```
sudo ./ati.run
```

---

### Post by bootsless999 on 2010-12-19
> **PhantmKllr said:**
> Try:
```
sudo ./ati.run
```

Nope. Still not working.

---

### Post by PhantmKllr on 2010-12-19
Right-click on the file and select "Properties". Under permissions tab, make sure that "Allow executing file as program" is checked. Then try it again.

---

### Post by bootsless999 on 2010-12-19
> **PhantmKllr said:**
> Right-click on the file and select "Properties". Under permissions tab, make sure that "Allow executing file as program" is checked. Then try it again.

Worked like a charm. Thanks.

---

### Post by PhantmKllr on 2010-12-19
Glad to help. :D Please mark the thread as solved if you haven't already. Thanks!

---

