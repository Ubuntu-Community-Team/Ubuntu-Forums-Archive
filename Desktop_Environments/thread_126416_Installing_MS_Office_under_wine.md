---
title: "Installing MS Office under wine"
date: 2006-02-06
forum: Desktop Environments
---

### Post by BlackJack on 2006-02-06
I am trying to install MS Office under wine and am having some problems. The install program starts ok and runs fine all the way through identifying what features you want to install. It then begins the actual installation and runs for about 30 seconds before it stops with a serries of errors. This happens even if i try the install as root.
Below is a copy of the terminal window that shows the errors.

Anybody have any ideas??

fixme:msi:deformat_component component key L"URL_Font_Color_Picker_ENU_X86.36432 36F_FC70_11D3_A536_0090278A1BB8"
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Common Files\\Microsoft Shared\\Visual Database Tools\\1033\\VDT70UI.DLL")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\CSSPKGUI.DLL")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\HTMEDUI.DLL")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\htmdlgsUI.dll")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\vsdebugui.dll")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\MSDBGUI.DLL")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\MSENVUI.DLL")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\vsbrowseUI.dll")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\VisualStudioTeamCoreUI.dll")
err:msi:deformat_file Unable to get ShortPath size (L"c:\\Program Files\\Microso ft Office\\OFFICE11\\VS Runtime\\1033\\CMDDEFUI.DLL")
err:msi:ITERATE_Actions Execution halted, action L"SKURED" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
root@D610:/home/tcotariu/Downloads/Office2003# fixme:imm:ImmDisableIME (-1): stu b
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 11"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00001388,(nil),0x000b,0x00 0000d6,0x300971b4,0x7c65cae4): stub
err:eventlog:ReportEventW L"office11setup"
err:eventlog:ReportEventW L"{90110409-6000-11d3-8cfe-0150048383c9}"
err:eventlog:ReportEventW L"11.0.5614.0"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_SETTEXTMODE: stub
fixme:richedit:RichEditANSIWndProc EM_SETTEXTMODE: stub
fixme:actctx:QueryActCtxW stub!

---

### Post by Orunitia on 2006-02-06
Why? Use openoffice, unless you have a very specific reason for wanting ms office.:???:

---

### Post by aysiu on 2006-02-06
There *are* some things MS Office does that OpenOffice can't, but they're very few. What functionality do you need that you think OpenOffice, KWord, and AbiWord can't handle?

Do you use a lot of macros?

---

### Post by BlackJack on 2006-02-06
Macros are not the issues. My issues are that in some documents the page formatting differs between MS Word and OpenOffice Writer, in Word a two page document sometimes extends to a third page in Open Office despite teh fact that the page settings seem to come over OK.

I also need to access 3 or 4 Access databases that do not come up in OpenOffice Base.

---

### Post by art on 2006-02-06
I think it is practically impossible to install Office with wine. Try Crossover Office tryal for free, I got MS Office 2003 install with no problem with version 5. As for Access it might not even work, which version do you have? Check here 
[http://www.codeweavers.com/site/compatibility/browse/name/?letter=a](http://www.codeweavers.com/site/compatibility/browse/name/?letter=a)

---

### Post by BlackJack on 2006-02-06
I am running Office 2003 and this is just about the last item on my list to figure out before converting to Linux 100%.

I have looked a bit at Crossover Office and is does list Office 2003 and all of it's apps (except Access) as being compatible, I was just hoping not to have to spend the $40.00 to do it if it would run under wine for free.

I also noticed that CodeWeavers does not list any games for compatibility (they all seem to be listed as "untested"). Have you run and Windows based games under it, and if so, how was it?

I will try downloading the 30 day eval this evening and see how it goes.

Thanks..........

---

### Post by BlackJack on 2006-02-06
Well, I just installed Crossover Office and then Office. The install went flawlessly and, as advertised, everything came up and worked with the exception of Access (not sure what I'll do to get around this).

Thanks for pointing me in this direction, I hate to us a virtual machine running Windows but will if I absolutely have to.

---

### Post by art on 2006-02-06
As for the games, I am not a gamer myself, but heard that cedega supports some. It's not free again...

---

### Post by art on 2006-02-06
Also check this out

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

they have a list of linux equivalents, maybe some will have what you need.

---

### Post by dickohead on 2006-02-06
As for why formatting differs between Office and OpenOffice, it's the fonts your using. Some fonts like Times New Roman and Arial are only available by installing them seperately to OpenOffice, I used to have the same gripe with Verdana, favourite font wasn't available with OpenOffice so I cracked it, but if you install them (search the forum for "windows fonts")_ the formatting should come out identical.

---

