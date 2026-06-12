---
title: "Problem installing unity greeter in Kubuntu."
date: 2012-12-19
forum: Desktop Environments
---

### Post by Devta on 2012-12-19
Hello everyone.

I'm running Kubuntu 12.10 with lightdm as the only window manager.

I installed all the dependencies for the unity manager and also installed the unity-greeter from synaptic package manager.
I then edited the lightdm.conf and set it to use the unity greeter.
Then I ran the command :```
lightdm --test-mode
```The xephyr window opened and closed.

When I set the greeter back to kde and tested it, it worked fine.

After that, I tried the manual install and on running ./configure, I got this:
```
devesh@3000-N100:~/Downloads/unity$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for valac-0.16... no
checking for valac... /usr/bin/valac
checking /usr/bin/valac is at least version 0.15.1... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make supports nested variables... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for UNITY_GREETER... no
configure: error: Package requirements (
    gtk+-3.0
    gdk-x11-3.0
    indicator3-0.4
    liblightdm-gobject-1 >= 1.3.3
    freetype2
    cairo-ft
    libcanberra
) were not met:

No package 'indicator3-0.4' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables UNITY_GREETER_CFLAGS
and UNITY_GREETER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
How do I set the environment variables:confused:?
Please tell me where I am going wrong.

---

### Post by oldos2er on 2012-12-20
You're missing several dependencies. Run ```
sudo apt-get build-dep unity-greeter
``` then retry ./configure

---

### Post by Devta on 2012-12-21
> **oldos2er said:**
> You're missing several dependencies. Run ```
sudo apt-get build-dep unity-greeter
``` then retry ./configure

The configure works but the login still does not work.

---

### Post by ianster_guy on 2013-01-21
Hi, this had actually even been a problem in a native Ubuntu install that had the Kubuntu desktop environment GUI installed. It seemed that Unity-greeter would not install or activate properly when that kubuntu package was installed. It seems the following commands where not fixing the issue: "sudo apt-get install --reinstall {PACKAGE}" packages like "unity-greeter" and-or "lightdm" Here is the link to the apparent fix [https://bugs.launchpad.net/unity-greeter/+bug/911826](https://bugs.launchpad.net/unity-greeter/+bug/911826) It would seem that after this fix one does not need to uninstall Kubuntu have untity-greeter run properly.

Though likely some people are here because they want to reinstall unity greeter, so here are some commands to get you started or help you search engine a better solution. 

```
sudo apt-get install --reinstall LightDM[CODE]

[CODE]sudo apt-get install --reinstall unity-greeter
``````
sudo gedit /etc/lightdm/lightdm.conf
```Where: "sudo" can be different to free programs from the terminal using "gksu {code} &" AND "gedit" can be your favorite text editor like "nano"

Change the line that starts with "greeter-session=" to
```
"greeter-session=unity-greeter"
```

---

