---
title: "stop lubuntu login screen to auto start"
date: 2012-10-21
forum: Desktop Environments
---

### Post by delqhi on 2012-10-21
there is one desktop in my office that is dual boot running ubuntu v.10 and ms-os (boot to grub). since last week, in my spare time, I try to fix it. the ms-os is infected by virus (what a surprise), because a co-worker bring her children to work and they installed any random games that internet can offer. obviously it got infected. so i wipe out that lame os.

but than i update ubuntu to kernel 3.2 and sudo apt-get install lubuntu, because unity reduce productive for office duty.

this is the first time i use lubuntu, so i know a little in how to configure it...

for example, every time i login, i got bombarded by unnecessary error pop-up along with request to report it. how to stop this auto report? the error is not that important, since after i close the report request, lubuntu just running fine.

i figure disabling as much as possible start-up service perhaps will solve the problem. mainmenu >preferences > desktop session setting offer less option than gnome-desktop start-up service setting. for example, i want to disable is vnc and openssh-server, desktop session setting, but i can not find it in desktop session setting. also, i want to disable auto login screen. in gnome-desktop i can disable gdm in start-up setting service. is there better menu in lubuntu that i can do that (mark or unmark which service that i want to run)?

i like when linux welcoming me with terminal and asking me to login to shell. in gnome-desktop, i will type sudo /etc/init.d/gdm start, if i want to move to desktop environment.

so..how to do that with lubuntu?

---

### Post by 2F4U on 2012-10-21
> for example, every time i login, i got bombarded by unnecessary error  pop-up along with request to report it. how to stop this auto report?

If you are sure that you want to ignore and disable the error reporting utility, edit /etc/default/apport and change the line that says

enabled=1

to

enabled=0

Save the file and reboot.

---

### Post by delqhi on 2012-10-22
thaks..i  already set it. no more error report.

the error came from gnome-panel. perhaps if I uninstall it, lubuntu will be just working fine...but for now, i just ignore it.

i guess i need to learn how to make lightdm to start manually, because even in gnome-desktop there no option to make any desktop manager not to start automatically (using GUI). perhaps it's because of unitiy, lot of nice app has been thrown away.

same thing with ssh server,  eed to learn  how to set it start manually using shell.

---

