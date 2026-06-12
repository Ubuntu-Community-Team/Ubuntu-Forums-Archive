---
title: "Wine doesn't work"
date: 2009-03-03
forum: General Help
---

### Post by Lord Butters I on 2009-03-03
I'm trying to get MS Office 2007 to work, I installed Wine, then did this: (copy/pasted from [here](http://www.detector-pro.com/2008/11/how-to-install-microsoft-office-2007-on.html)
# On Aplications tab, Windows Version select Windows Vista.
# Go to Libraries tab, than New override for library, select rpcrt4.dll - click Add, and msxml3.dll - click Add again and use edit for both files to make them Native(Windows)

Now nothing wine related will work.  When I try to open winecfg from the terminal I get this:

err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

I even uninstalled Wine and reinstalled it, but the problem persisted.  Help!

---

### Post by lykwydchykyn on 2009-03-03
To bring wine back to default settings, rename (or delete, if you don't care about losing your old settings completely) the ~/.wine folder.

When you re-run wine, it will recreate a default setup.

---

### Post by Lord Butters I on 2009-03-03
Noob question time... How do I do that?

NVM figured it out.  I can open winecfg now!

---

### Post by handy on 2009-03-03
This thread would do far better in the Wine sub-forum.

I'll ask the mod's to move it for you OP.

---

