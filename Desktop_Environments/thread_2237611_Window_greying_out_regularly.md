---
title: "Window greying out regularly"
date: 2014-08-02
forum: Desktop Environments
---

### Post by netsurfau on 2014-08-02
This issue started in 13.10 and has gotten worse in 14.04

The active window will grey out and hang for up to a minute.  Any other open windows are accessible and will operate.
I've only ever had one error message when this has happened and it referred to a video driver problem.

System Specs.

AMD Phenom Quad Core 3GHZ
4Gb RAM
512Mb nVidea 8400 Series Video Card

I cannot see any logical reason for this to be happening with the amount of RAM, and the fact it usually happens to either
Thunderbird, Google Chrome browser or Libre Office Calc (the three apps I use the most), but has happened with other
apps randomly.

Ideas?

---

### Post by veddox on 2014-08-03
When I first switched to 14.04 I encountered the same problem a lot with Opera. Eventually I remembered that I had forgotten to add swap during install, so I created a swap file and since then, it's been running a lot smoother (though it still happens occasionally). I have 4gb RAM just like you, but I found that when I was running my browser (I keep a LOT of tabs open) plus Unity plus other programs, it was a bit too much for my computer - swap alleviated the problem. To check whether that might be your issue, open the system monitor and have a look at the Resources -> Memory and swap history.

---

### Post by netsurfau on 2014-08-05
Thanks Veddox,

I had already set up a 1Gb swap partition, and only had four active apps running - Thunderbird, Chrome, Libre Calc & Deluge Bit Torrent Client.

After seeing your reply, I had System Monitor running, and the only change it showed was a drop in incoming data for my Internet connection.
System Monitor also showed about 1.8Gb of RAM being used & less than 1Gb of Swap. So, to me, this doesn't seem to be an available resources issue but, something else.

Does anyone else have any ideas?

---

### Post by netsurf on 2014-09-13
This problem is becoming more & more regular, predominately in Google Chrome (which I probably use the most).

I've decided to try & resolve it by wiping my primary drive & doing a clean install of 14.04.

My problem now is, my second 500Gb drive has the permissions set to "root" only, and I cannot remember how to change
the permissions for the drive so I can back up my Home directory, before formatting the boot drive & re-installing.

Could someone help with this?

---

### Post by grahammechanical on 2014-09-14
The greying out of an application window is the Ubuntu equivalent of the Microsoft hour glass. It means that the application is busy. It does not mean that there is no free memory or that the CPU is running at maximum load.

To prove this install System Load Indicator it will show that the CPU is not under maximum load or that there is still free memory. System Monitor (default installed) should also show this.

Regards.

---

### Post by netsurfau on 2014-10-24
@grahammechanical

I installed the System Load indicator and every time I got a greying out of a window it showed the CPU load at 3-4% & "iowait" at 95%+.  Also, the overall "Load" would increase, sometimes to well over a value of 12.

Based on what you wrote, I think there was something else causing this issue.  My system crashed yesterday & I've lost all access to my original C Drive.  Once I've managed to recover the data from it, I'm going to do 
a clean install & "start from scratch", and see if the issue returns.

Thanks a lot for your help.

---

