---
title: "Fuzzy Display Until Screensaver Timeout?"
date: 2020-08-10
forum: Desktop Environments
---

### Post by sdholmes on 2020-08-10
[FONT=arial][COLOR=#24292E]I have Xubuntu 20.04 installed on some "thin" client machines - mostly 4-core AMD SOCs (CPU Passmark > 2000) with various Radeon graphics eg: 8330E, 8280E, R5E, etc.
There was no sign of the problem with 5.4.0-26-generic but after 5.4.0-40 I find they have a fuzzy (but readable) display of LightDM, and if I login, the desktop and everything else in Xubuntu is fuzzy and stays fuzzy. But if I leave LightDM to timeout to a blank screen (10 minutes by default) then move the mouse, LightDM is now sharp and logging in to Xfce all remains sharp.
The timeout appears to be the X Screensaver - the only config I found to change it was to put[/COLOR][/FONT]
[FONT=lucida console]Section "ServerFlags"
    Option "BlankTime" "1"
EndSection[/FONT]
[FONT=arial][COLOR=#24292E]into an xorg.conf file eg: /etc/X11/xorg.conf.d/50-BlankTime.conf
as suggested here: [https://shallowsky.com/linux/x-screen-blanking.html](https://shallowsky.com/linux/x-screen-blanking.html)
This workaround reduces the timeout to one minute so that users only have to wait 1 min for the screen to blank before they can login. (I then have to turn off DPMS with xset -dpms in each user's ~/.xsessionrc to prevent a 1 min timeout by the Xfce screensaver).
$ inxi -G at a virtual console shows the same correct info eg: Radeon driver model, resolution, etc, when the screen is fuzzy and when it is sharp.
Anyone have any ideas why this fuzzy display is happening, and why the redisplay after X blanking fixes it?[/COLOR][/FONT]

---

