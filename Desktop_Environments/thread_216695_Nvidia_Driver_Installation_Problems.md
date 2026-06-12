---
title: "Nvidia Driver Installation Problems"
date: 2006-07-15
forum: Desktop Environments
---

### Post by uab999 on 2006-07-15
When I first installed the nvidia driver, I thought I needed the legacy driver (I don't know why).  So, I installed the legacy driver using tseliot's guide at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper").
The driver was installed and it worked great.  Then I realized that I didn't need the legacy driver and I wanted to install the regular glx driver instead.  I uninstalled the legacy driver and installed the glx driver.  When I went to the terminal to execute the command 'sudo nvidia-glx-config enable', it gave me the following message: 
> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

I don't exactly know what this means, but I checked the xorg.conf file and the driver section already had "nvidia", not "nv".  So I'm not sure what it 's asking for.  Somehow, I lost the backup file I created, so I used the command "sudo dpkg -reconfigure -phigh xserver-xorg".  When I restarted the computer, I tried to enable the driver and got the same message as above.  Then I followed the instructions in tseliot's guide again (this time for the glx driver), but I still get the error when I try to enable the driver.  I'm sorry this was so long-winded, but my real problem is that I can't tell if the driver is working or not and if it's not, I don't know how to fix it.  
So, is there a way to check if it is enabled or how can I fix the above problem?  Thank you very much in advance.

---

### Post by Dr. Nick on 2006-07-15
If your xorg.conf driver is set to nvidia then the script will give that error, You dont necessarilly have to run the script to complete the installation of the driver, all the script will do is change it from nv to nvidia (which it already is)

So if your xorg.conf is at nvidia already then forget about the script, you are fine.
Their are a few commands to run to test the driver, I forget them at the moment. The way I test is just look for the nvidia screen on boot, and try out a few opengl applications/screensavers

---

