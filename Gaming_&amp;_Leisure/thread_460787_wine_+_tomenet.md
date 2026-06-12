---
title: "wine + tomenet???"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by richieboy on 2007-06-01
i thought i was past the noob stage, but...

i want to try tomenet in wine because someone told me the windows display was better.  i extracted the files to:

/~/.wine/drive_c/windows/system 32/ and tried wine tomenet4.exe on command line.  i get this output:


wine: could not load L"c:\\windows\\system32\\tomenet4.exe": Module not found
rich1@monosBackForty:~$ wine tomenet4.exe
fixme:process:IsWow64Process (0xffffffff 0x70fcfc) stub!
fixme:advapi:ImpersonateLoggedOnUser ((nil))
err:ntdll:NtQueryInformationToken Unhandled Token Information class 8!
fixme:advapi:ImpersonateLoggedOnUser ((nil))
err:ntdll:NtQueryInformationToken Unhandled Token Information class 8!
err:ntdll:RtlpWaitForCriticalSection section 0x7bc823a4 "loader.c: loader_section" wait timed out in thread 000a, blocked by 0009, retrying (60 sec)
fixme:advapi:ImpersonateLoggedOnUser ((nil))
err:ntdll:NtQueryInformationToken Unhandled Token Information class 8!
fixme:ntdll:NtQueryObject Unsupported information class 1
fixme:ntdll:NtQueryObject Unsupported information class 1
     15 [main] tomenet4 -8 handle_exceptions: Exception: STATUS_CONTROL_C_EXIT
    470 [main] tomenet4 -8 open_stackdumpfile: Dumping stack trace to tomenet4.exe.stackdump
err:seh:setup_exception stack overflow 36 bytes in thread 0009 eip 7bc63702 esp 00500fdc stack 0x501000-0x710000


you can see where i ^c to stop but it just freezes there and becomes a zombie process that i can't kill.  please help me, obi wan ubuntu.  you're my only hope.:)

thanks,
rich

---

