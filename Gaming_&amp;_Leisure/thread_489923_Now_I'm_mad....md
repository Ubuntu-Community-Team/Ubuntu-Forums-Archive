---
title: "Now I'm mad..."
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by toasty_ghosty on 2007-07-01
So I had Steam working..had. And I went to start it again and I got this in console:

Xlib: extension "XFree86-DRI" missing on display ":0.0".
Xlib: extension "XFree86-DRI" missing on display ":0.0".

Then I started Steam and got this:

Steam.exe (main exception): Cannot open blob archive file: CMultiFieldBlob(mem-mapped file): Failed to open exisitingfile, Win32 Error 5 "Access denied"

So I thought I would reinstall Steam. I uninstalled it from the Wine uninstaller and began installing it again. In the console I got 

Xlib: extension "XFree86-DRI" missing on display ":0.0".
Xlib: extension "XFree86-DRI" missing on display ":0.0".

all over again. So I continued on and once again got 

Steam.exe (main exception): Cannot open blob archive file: CMultiFieldBlob(mem-mapped file): Failed to open exisitingfile, Win32 Error 5 "Access denied"

all over again. But I could still install it so I continued on. The next thing I know I'm getting all of this:

theking@OptimusPrimeTheSecond:~$ wine /home/theking/Desktop/Steaminstall.exe
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF604.tmp") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF607.tmp") : returns fake SECURITY_DESCRIPTOR
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:advapi:GetFileSecurityW (L"C:\\Program Files\\Steam\\UNWISE.EXE") : returns fake SECURITY_DESCRIPTOR

What the heck?! Whats going on? Why won't it work? Did I piss off the linux gods? I'm sorry to complain. But this is somewhat frustrating. No not somewhat. It is.

---

### Post by FoolsGold_MKII on 2007-07-01
Wine update perhaps? 0.9.40 was released recently, maybe you updated and things blew up.

Perhaps they stuffed up something again, happens often enough.

---

### Post by cogadh on 2007-07-01
Did you try following the Steam How-To on Wine's website:
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)
Scroll down about halfway, you can't miss it.

---

### Post by toasty_ghosty on 2007-07-01
But when I run it I get this still:
          Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Does that mean that my ATI drivers arnt being used? How do I fix that?

and when I do:

wine iexplore [http://winehq.org](http://winehq.org)

to install the gecko drivers I get:

theking@OptimusPrimeTheSecond:~$ wine iexplore [http://winehq.org](http://winehq.org)
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:shdocvw:IEWinMain "http://winehq.org" 1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:ole:CoResumeClassObjects stub
err:ole:CoGetClassObject apartment not initialised
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x18cce4)->((null) 1 0x33faec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18cce4)->((null) 25 2 0x33fb00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18cce4)->((null) 26 2 0x33fb00 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x18cce4)->(0x33fb3c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18cce4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fc60 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x18db98)->(L"" L"" 0 0x33fc74)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x18db98)->(0x33fc78 0x33fb9c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18cce4)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x18cce4)
fixme:shdocvw:ClientSite_GetContainer (0x18cce4)->(0x33fb8c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x18cce4)->(0xb7e89f49)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18cce4)->((null) 25 2 0x33fac8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18cce4)->((null) 26 2 0x33fac8 (nil))
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002

I keep getting that same error.

What am I doing wrong?

---

### Post by toasty_ghosty on 2007-07-02
And I have no idea how those smile things got there....I'm not doing well.
And to be honest I just want to start all over again. How would I just delete all the Steam data and start fresh?

---

### Post by FoolsGold_MKII on 2007-07-02
> **toasty_ghosty said:**
> And to be honest I just want to start all over again. How would I just delete all the Steam data and start fresh?
If Steam is the only program you're using Wine for, you can simply delete the **.wine** folder from your home folder. That would delete Steam (which would have been installed in that folder by default), as well as things like registry settings.

Afterwards it's just a matter of running winecfg to create a clean new .wine folder, set the necessary configs and install Steam.

---

### Post by toasty_ghosty on 2007-07-02
I tried that but it is telling me I do not have permission to delete it because:

"/home/theki...teamUI.dll" cannot be deleted because you do not have permissions to modify its parent folder

How do I get around that? But if I just leave it in the trash and create a new one I get:

theking@OptimusPrimeTheSecond:~$ winecfg
wine: creating configuration directory '/home/theking/.wine'...
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
wine: '/home/theking/.wine' created successfully.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet


What?

---

### Post by cogadh on 2007-07-02
Try using the forum CODE tags when you post the output from the terminal, that will get rid of the smilies.

When you installed Steam or when you ran "winecfg" did you use the "sudo" command? If so, don't do that. That give the files in Wine root permissions, which could be causing your delete issues.

Run this in a terminal to check the status of your video driver:
```
glxinfo | grep direct
```
It should come back saying "Direct Rendering yes", if it doesn't, then your accelerated 3D driver is not enabled.

---

