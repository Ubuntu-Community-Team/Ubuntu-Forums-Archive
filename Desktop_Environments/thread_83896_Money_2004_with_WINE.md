---
title: "Money 2004 with WINE"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Jerrac on 2005-10-29
I am trying to install Money 2004 with the latest version of WINE avaible through the repositories. It freezes on the Checking for components and disk space window. This is the output in the terminal I get:> firstuser@jerrac:~$ cd /media/cdrom
firstuser@jerrac:/media/cdrom$ wine setup.exe
err:msi:MsiEnableLogW Unable to enable log L"C:\\mnyscost.log"
fixme:msi:MsiInstallProductW L"Z:\\media\\cdrom0\\SysPack.Msi" L" RUN_PRECOST=1 REBOOT=ReallySuppress"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!
fixme:advapi:DecryptFileA "C:\\msdownld.tmp\\IXP003.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\msdownld.tmp\\IXP003.TMP\\IESetup.inf" "Options.WIN" "Options.WIN" "InstallDir" 0x10252d8 260 0x7fb1f830 (nil)): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\msdownld.tmp\\IXP003.TMP\\IESetup.inf", "ActiveX", "C:\\msdownld.tmp\\IXP003.TMP", (null), (nil), 0x0000000d, (nil)): stub
wine: Unhandled exception (thread 000f), starting debugger...
Usage: winedbg [--command cmd|--auto] [--gdb [--no-start] [--with-xterm]] cmdline
err:seh:EXC_DefaultHandling Unhandled exception code c000013a flags 0 addr 0xffffe40e
firstuser@jerrac:/media/cdrom$


Any suggestions?

---

### Post by Jerrac on 2005-11-02
Anybody?

---

### Post by kperkins on 2005-11-02
You might be better off using crossover office than wine.
Why use Money at all though when there are several alternatives that work wonderfully, natively, on Linux, and can import your money files (save as QIFs)?

---

### Post by HermanAB on 2005-11-02
You could use Gnu Cash.  It is very similar:
[http://www.aerospacesoftware.com/GNU_Cash_for_Business_users_Howto_Guide.html](http://www.aerospacesoftware.com/GNU_Cash_for_Business_users_Howto_Guide.html)

Otherwise, try an older copy of Money on CxOffice.  I am running QuickBooks Pro 6.0 on CxOffice.  Even though I wrote a guide on doing it, switching is just too much hassle...

---

### Post by Jerrac on 2005-11-03
I don't want to spend sixty dollars on crossover office. Or however much it is... 

As for switching programs, I just haven't found one that is good enough. Money just works for me. Other than the fact that it is microsoft... Heh.

---

### Post by kperkins on 2005-11-05
I use Moneydance.  It's not free (beer{about $30}, or freedom), but it's not Money (therefore not MS) and it works natively on Linux, as well as Windows (and Mac, I think), and does everything that I ever wanted Money to do, and more.

---

### Post by andlinux21 on 2005-11-05
That moneydance looks pretty good I think I will have to get a copy :KS

---

### Post by JuanC on 2005-11-05
MoneyDance have an amd64 version?

MoneyDance has Internationalization , support for many languages?

---

### Post by Jerrac on 2005-11-05
I have tried the demo of money dance. I don't really like it...

Does anyone know what the messages printed out from the terminal mean?

---

