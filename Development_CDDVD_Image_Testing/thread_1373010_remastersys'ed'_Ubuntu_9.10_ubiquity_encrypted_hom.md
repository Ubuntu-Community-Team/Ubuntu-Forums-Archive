---
title: "remastersys'ed': Ubuntu 9.10 ubiquity encrypted homedir install FAIL"
date: 2010-01-05
forum: Development CD/DVD Image Testing
---

### Post by walterav on 2010-01-05
Making a custom-distro with remastersys is very easy, except one feature of the ubiquity installer gets killed. 
Its the option for 'encrypted homedir' install/login. 

When you boot of your custom-distro.iso and install just select the manual login with encrypted homedir checkbox and the installer will hang/crash at around80%. I tried to do a bug report but aport stops and says this is not a official ubuntu package. Doing the same with LinuxMint8 gives me some kind of error report. Its posted on the remastersys forum:
[http://geekconnection.org/remastersys/forums/index.php?topic=482.0](http://geekconnection.org/remastersys/forums/index.php?topic=482.0)

Can I report this as a ubiquity bug? Or is this just unsupported?

---

### Post by walterav on 2010-01-23
> **walterav said:**
> Making a custom-distro with remastersys is very easy, except one feature of the ubiquity installer gets killed. 
Its the option for 'encrypted homedir' install/login. 

When you boot of your custom-distro.iso and install just select the manual login with encrypted homedir checkbox and the installer will hang/crash at around80%. I tried to do a bug report but aport stops and says this is not a official ubuntu package. Doing the same with LinuxMint8 gives me some kind of error report. Its posted on the remastersys forum:
[http://geekconnection.org/remastersys/forums/index.php?topic=482.0](http://geekconnection.org/remastersys/forums/index.php?topic=482.0)

Can I report this as a ubiquity bug? Or is this just unsupported?

I discoverd that the install fails at a earlier stage, as soon as it fills /target/dev/.

The encrypted home installer fails to fill /target/dev/ with devices and folders only the file null is created. As soon as I create a folder called 'shm' the installer waits at 83% instead of the crash, it also creates a /target/home/user folder with some ecryptfs stuff, which will not take place if I won't put in the 'shm' folder myself.

What I think is that the installer fails in a much earlier stage, around 20% and when it detects there is no /dev/shm/ecryptetcetc it fails at 83%.
I just don't know which script takes care of filling /target/dev/.

anyone?

---

