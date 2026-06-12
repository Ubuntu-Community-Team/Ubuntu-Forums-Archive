---
title: "intel graphics with wayland black screen after login"
date: 2019-01-04
forum: Desktop Environments
---

### Post by kingpenguin on 2019-01-04
I was wondering because I have a Dell Optiplex 7040 with ubuntu 18.10 and after I login I get a black screen on my left monitor but the right one works fine. After I turned off wayland and reverted back to xorg it works as expected. Is there someway to get wayland to work or is there really a point in trying to get wayland working? I know just enough to really be dangerous in Linux but have a background in computer science so I do not mind messing around. I know that xorg is stupid old in software age perspective but I do not know enough about wayland to really understand what is changing. I am kinda curious to find out what is going on. The only thing that has happened with my Ubuntu 18.10 is I installed yesterday and did a full update in a tty because the graphic glitch. Then I modified a config file to disable wayland to get my desktop working. Other than that this Ubuntu is fully stock with not even a single application installed. I am running Kernel 4.18 but I am currently at work so i can not tell you the minor revision. Just trying to get some ideas before I go home.

---

### Post by kingpenguin on 2019-01-04
Never mind I have had to many bugs with ubuntu 18.10 I am just going to try a different distro.

---

### Post by speartip on 2019-01-09
You need to stick with the LTS versions of Ubuntu if you want Stability. 18.04 is the way to go. There you will find it uses Xorg as default, because as you have realized Wayland is still too buggy at present.
It is likely that Wayland will be default in the 20.04 LTS version, as by then the issues will probably have been ironed out.

---

