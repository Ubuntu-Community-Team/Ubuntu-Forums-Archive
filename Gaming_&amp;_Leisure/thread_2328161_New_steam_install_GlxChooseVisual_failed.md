---
title: "New steam install GlxChooseVisual failed"
date: 2016-06-18
forum: Gaming &amp; Leisure
---

### Post by arcticchambers on 2016-06-18
Hey folks. 

I've been searching the ubuntu forums for a soloution here to no avail. 
I'm running Ubuntu 16.04 lts with an Amd cpu 9590 and a gtx 660 video card.

I'm trying to install steam on my machine and i keep getting the error glx choose visual failed.
 When I run in Terminal i get this:

tyler@LinuxBox:~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1465948400)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
glXChooseVisual failedMain.cpp (310) : Assertion Failed: Fatal Error: glXChooseVisual failed
Assert( Assertion Failed: Fatal Error: glXChooseVisual failed ):Main.cpp:310

Installing breakpad exception handler for appid(steam)/version(1465948400)
[0617/214746:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
[0617/214746:ERROR:browser_main_loop.cc(217)] Running without the SUID sandbox! See [https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md](https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md) for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160614232302)
Installing breakpad exception handler for appid(steamwebhelper)/version(1465946582)
[0617/214746:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
assert_20160617214746_6.dmp[21561]: Uploading dump (out-of-process)
/tmp/dumps/assert_20160617214746_6.dmp
Installing breakpad exception handler for appid(steamwebhelper)/version(20160614232302)
Installing breakpad exception handler for appid(steamwebhelper)/version(1465948400)
Installing breakpad exception handler for appid(steamwebhelper)/version(1465948400)
assert_20160617214746_6.dmp[21561]: Finished uploading minidump (out-of-process): success = yes
assert_20160617214746_6.dmp[21561]: response: CrashID=bp-adfc4ef7-b682-47da-b135-2284f2160617
assert_20160617214746_6.dmp[21561]: file ''/tmp/dumps/assert_20160617214746_6.dmp'', upload yes: ''CrashID=bp-adfc4ef7-b682-47da-b135-2284f2160617''


I tried changing the video card driver to the latest proprietary tested driver, but with no luck. 

Can anyone help me here?
Thanks

---

### Post by xen3 on 2016-06-18
Did you use Ubuntu steam or the package provided by Steam? It might not make a difference, but they do different things, particularly with regards to locations and such.

nVidia is notorious with the latest driver for requiring all kinds of extra parameters, but this mostly relates to games, I have not had it fail for the client itself yet.

So if anything, changing it to an older proprietary driver, might help more ;-). Other than that, maybe they know at Steam..... there is an #ubuntu-steam channel, but I don't know if it is much useful.

Did Steam download its 240 meg worth of updates, to begin with? Ha, I'm getting the same error, let's see if I can solve it....

Well, **a reboot fixed it**.

---

