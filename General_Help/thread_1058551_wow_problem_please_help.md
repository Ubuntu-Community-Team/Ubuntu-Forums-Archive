---
title: "wow problem please help"
date: 2009-02-02
forum: General Help
---

### Post by bigschwanz9 on 2009-02-02
austin@champ:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7e070000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e070000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x3aedb0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aece4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af2cc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af594,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af590,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af514,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af514,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af00c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af144,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf10,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf38,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x374028c4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub


My internet is good, but when it gets to the login screen its black except for a few gray lines. The wow hand is there though. I have 7.10 ubuntu.

---

### Post by Agent ME on 2009-02-02
I would say for you to upgrade wine ( [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") ), but they only have downloads for 8.04 and 8.10, and I don't think it's worth it to build wine yourself.
You should upgrade to 8.10, and then install the latest wine.

---

