---
title: "Steam GUI freezing"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by MattThLinuxNewb on 2007-03-19
Hey, i've been trying to get Steam running via wine but have run into a problem and can't seem to get any further... I can log in fine (no font problems, etc), and after some time the main interface appears, but it freezes every time without fail after a few seconds...

Screenshot of (unresponsive) window:

[[img=http://img137.imageshack.us/img137/7159/steamyg5.th.png]](http://img137.imageshack.us/my.php?image=steamyg5.png)

And here's the console output:
```

matt@matt-desktop:~/Windoze/Steam$ wine steam.exe
You need to install the Mozilla ActiveX control to
use Wine's builtin CLSID_WebBrowser from SHDOCVW.DLL
fixme:shdocvw:ViewObject_SetAdvise (0x7cadfca8)->(1 00000002 0x6faf2ad8)
fixme:shdocvw:PersistStreamInit_InitNew (0x7cadfca8)
fixme:shdocvw:WebBrowser_put_MenuBar (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_AddressBar (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_StatusBar (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_ToolBar (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x7cadfca8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x7cadfca8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0x7cadfca8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Visible (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(24)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(64)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(24)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(64)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(24)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(64)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Visible (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Visible (0x7cadfca8)->(0)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:shdocvw:WebBrowser_put_Height (0x7cadfca8)->(772)
fixme:shdocvw:WebBrowser_put_Width (0x7cadfca8)->(895)
fixme:mshtml:HTMLDocument_get_body (0x6a6d1eb0)->(0x7fb9dc5c)
fixme:shdocvw:WebBrowser_put_Visible (0x7cbf0d98)->(0)

```

I followed these two guides:
[https://help.ubuntu.com/community/CounterStrike](https://help.ubuntu.com/community/CounterStrike)
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

I'm using Ubuntu 6.06, with an amd 64bit 3200+ cpu, geforce 6600gt graphics and the nvidia driver if that's relevant

:(  Any help would be great, im at a loss here

Thanks, Matt

---

### Post by MattThLinuxNewb on 2007-03-20
Wow I can't believe i got it working! Here's what I did in case anyone else has this problem:
It seems the mozilla activex component is actually required for the steam window to work. All I had to do was follow the configure section of the guide. ([http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games))
In my case this meant downloading [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz), copying it to a folder in wine's drive_c directory and running
```

wine regsvr32 mozctlx.dll

```

---

