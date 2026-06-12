---
title: "NAMO WebEditor Suite"
date: 2009-05-14
forum: General Help
---

### Post by grtwhiterhyno on 2009-05-14
I hope I am posting in the right place, let me know if I am and I'll fix it.

I have just installed NAMO WebEdidtor 06 edition.  I was hoping wine would just open it and everything would remain peachy keen and the world would continue to spin aloft through space and everyone be happy and joyful.  Nope.

The WebEditor will not even make an attempt to open and the NAMO FreeMotion flash editor which I reeeeally want to play with, opens for all of 1 second before disappearing into the atmosphere.  Joy.  What am I missing here?  Should I update wine?  Am I missing something from my synaptic repertoire?  Please make hast with any help you may be able to supply.

Your local rhino in need.

---

### Post by Mirge on 2009-05-14
Open it with a terminal window and paste the error here.

---

### Post by grtwhiterhyno on 2009-05-14
My dear and wonderful friend, though I know how to open terminal, my experience ends there.  If you could help me with how to accomplish that mystical feat I would be glad to accomodate.

---

### Post by grtwhiterhyno on 2009-05-17
ok, so in order to get to the directory that contained the .exe file, i had to do quite a bit of tinkering. the folder was hidden, took me a minute to figure out you could get to it even though it isnt listed in the dir. then a couple of the folders had spaces in the name, i.e.: Program Files, so i had to insert an underscore.
but i finally got it done and here it is, let me know what you think cuz it hurts my eyes to look:

############:~/.wine[/email][/email]/drive_c/Program_Files/Namo/WebEditor_2006/bin$ wine WebEditor.exe
errle:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
errle:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x7acdb
fixmele:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:imagehlp:ImageLoad (WebEditor.exe, C:\Program_Files\Namo\WebEditor_2006\bin): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x427bc9 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00427bc9).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:00427bc9 ESP:0032ee34 EBP:0032eebc EFLAGS:00010246( - 00 -RIZP1)
EAX:00000000 EBX:0073d620 ECX:cdcdcdcd EDX:00a7004c
ESI:00a70118 EDI:00000000
Stack dump:
0x0032ee34: 00000000 0073c680 0032f7bc 0032f794
0x0032ee44: 00000020 6c3c6700 01c763a5 de124880
0x0032ee54: 01c9d6b3 6c3c6700 01c763a5 00000000
0x0032ee64: 00343000 00000000 defb639a 45626557
0x0032ee74: 6f746964 78652e72 8d990065 8d9502df
0x0032ee84: 8d9b1e5d 8d9502df 8d9f2083 8d9502db
Backtrace:
=>1 0x00427bc9 in webeditor (+0x27bc9) (0x0032eebc)
2 0x8d9502df (0x8d912221)
0x00427bc9: cmpl %ecx,0x0(%eax)
Modules:
Module Address Debug info Name (106 modules)
PE 400000- 84a000 Export webeditor
PE c90000- fc3000 Deferred weenu
PE 5d360000-5d36e000 Deferred mfc80enu
PE 60200000-60225000 Deferred ssce5332
PE 61a00000-61b31000 Deferred gear81sd
PE 61c00000-61c0c000 Deferred iglzw32s
PE 78130000-781cb000 Deferred msvcr80
PE 781d0000-782df000 Deferred mfc80
ELF 7b800000-7b92d000 Deferred kernel32<elf>
\-PE 7b820000-7b92d000 \ kernel32
ELF 7bc00000-7bca4000 Deferred ntdll<elf>
\-PE 7bc10000-7bca4000 \ ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
PE 7c420000-7c4a7000 Deferred msvcp80
ELF 7dfb9000-7dfcf000 Deferred msimtf<elf>
\-PE 7dfc0000-7dfcf000 \ msimtf
ELF 7dfcf000-7dfd3000 Deferred libgpg-error.so.0
ELF 7dfd3000-7e020000 Deferred libgcrypt.so.11
ELF 7e020000-7e030000 Deferred libtasn1.so.3
ELF 7e030000-7e033000 Deferred libkeyutils.so.1
ELF 7e033000-7e065000 Deferred libcrypt.so.1
ELF 7e065000-7e0db000 Deferred libgnutls.so.13
ELF 7e0db000-7e0fe000 Deferred libk5crypto.so.3
ELF 7e0fe000-7e18b000 Deferred libkrb5.so.3
ELF 7e18b000-7e1b4000 Deferred libgssapi_krb5.so.2
ELF 7e1b4000-7e1e7000 Deferred libcups.so.2
ELF 7e24a000-7e27d000 Deferred uxtheme<elf>
\-PE 7e250000-7e27d000 \ uxtheme
ELF 7e27d000-7e286000 Deferred libxcursor.so.1
ELF 7e286000-7e28b000 Deferred libxfixes.so.3
ELF 7e28b000-7e28e000 Deferred libxcomposite.so.1
ELF 7e28e000-7e294000 Deferred libxrandr.so.2
ELF 7e294000-7e29c000 Deferred libxrender.so.1
ELF 7e29c000-7e29f000 Deferred libxinerama.so.1
ELF 7e29f000-7e2bf000 Deferred imm32<elf>
\-PE 7e2b0000-7e2bf000 \ imm32
ELF 7e2bf000-7e2c4000 Deferred libxdmcp.so.6
ELF 7e2c4000-7e2dc000 Deferred libxcb.so.1
ELF 7e2dc000-7e2de000 Deferred libxcb-xlib.so.0
ELF 7e2de000-7e3c5000 Deferred libx11.so.6
ELF 7e3c5000-7e3d3000 Deferred libxext.so.6
ELF 7e3d3000-7e3eb000 Deferred libice.so.6
ELF 7e3eb000-7e3f3000 Deferred libsm.so.6
ELF 7e3f4000-7e3fc000 Deferred libkrb5support.so.0
ELF 7e3fc000-7e3ff000 Deferred libcom_err.so.2
ELF 7e401000-7e498000 Deferred winex11<elf>
\-PE 7e410000-7e498000 \ winex11
ELF 7e4cf000-7e4f0000 Deferred libexpat.so.1
ELF 7e4f0000-7e51a000 Deferred libfontconfig.so.1
ELF 7e51a000-7e51d000 Deferred libxau.so.6
ELF 7e528000-7e53d000 Deferred libz.so.1
ELF 7e53d000-7e5aa000 Deferred libfreetype.so.6
ELF 7e5ab000-7e5b0000 Deferred libxxf86vm.so.1
ELF 7e5b8000-7e5d9000 Deferred mpr<elf>
\-PE 7e5c0000-7e5d9000 \ mpr
ELF 7e5d9000-7e627000 Deferred wininet<elf>
\-PE 7e5e0000-7e627000 \ wininet
ELF 7e627000-7e666000 Deferred urlmon<elf>
\-PE 7e630000-7e666000 \ urlmon
ELF 7e666000-7e708000 Deferred oleaut32<elf>
\-PE 7e680000-7e708000 \ oleaut32
ELF 7e708000-7e769000 Deferred rpcrt4<elf>
\-PE 7e710000-7e769000 \ rpcrt4
ELF 7e769000-7e80d000 Deferred ole32<elf>
\-PE 7e780000-7e80d000 \ ole32
ELF 7e80d000-7e824000 Deferred imagehlp<elf>
\-PE 7e810000-7e824000 \ imagehlp
ELF 7e824000-7e837000 Deferred libresolv.so.2
ELF 7e845000-7e863000 Deferred iphlpapi<elf>
\-PE 7e850000-7e863000 \ iphlpapi
ELF 7e863000-7e88f000 Deferred ws2_32<elf>
\-PE 7e870000-7e88f000 \ ws2_32
ELF 7e88f000-7e8a9000 Deferred wsock32<elf>
\-PE 7e890000-7e8a9000 \ wsock32
ELF 7e8a9000-7e913000 Deferred msvcrt<elf>
\-PE 7e8c0000-7e913000 \ msvcrt
ELF 7e913000-7e927000 Deferred lz32<elf>
\-PE 7e920000-7e927000 \ lz32
ELF 7e927000-7e940000 Deferred version<elf>
\-PE 7e930000-7e940000 \ version
ELF 7e940000-7e976000 Deferred winspool<elf>
\-PE 7e950000-7e976000 \ winspool
ELF 7e976000-7e9cf000 Deferred shlwapi<elf>
\-PE 7e980000-7e9cf000 \ shlwapi
ELF 7e9cf000-7eae2000 Deferred shell32<elf>
\-PE 7e9e0000-7eae2000 \ shell32
ELF 7eae2000-7eb8d000 Deferred comdlg32<elf>
\-PE 7eaf0000-7eb8d000 \ comdlg32
ELF 7eb8d000-7ebdf000 Deferred advapi32<elf>
\-PE 7eba0000-7ebdf000 \ advapi32
ELF 7ebdf000-7ec7a000 Deferred gdi32<elf>
\-PE 7ebf0000-7ec7a000 \ gdi32
ELF 7ec7a000-7edc1000 Deferred user32<elf>
\-PE 7ec90000-7edc1000 \ user32
ELF 7edc1000-7ee80000 Deferred comctl32<elf>
\-PE 7edd0000-7ee80000 \ comctl32
ELF 7efa0000-7efab000 Deferred libnss_files.so.2
ELF 7efab000-7efb5000 Deferred libnss_nis.so.2
ELF 7efb5000-7efcd000 Deferred libnsl.so.1
ELF 7efcd000-7eff2000 Deferred libm.so.6
ELF 7eff7000-7f000000 Deferred libnss_compat.so.2
ELF b7c86000-b7c8a000 Deferred libdl.so.2
ELF b7c8a000-b7dd9000 Deferred libc.so.6
ELF b7dd9000-b7df1000 Deferred libpthread.so.0
ELF b7dff000-b7f35000 Deferred libwine.so.1
ELF b7f37000-b7f53000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) C:\Program_Files\Namo\WebEditor_2006\bin\WebEditor .exe
00000009 0 <==
0000000c
0000001a 0
00000019 0
00000013 0
00000012 0
0000000e 0
0000000d 0
0000000f
00000015 0
00000014 0
00000011 0
00000010 0
00000016
0000001b 0
00000018 0
00000017 0
0000001c
0000001d 0
Backtrace:
=>1 0x00427bc9 in webeditor (+0x27bc9) (0x0032eebc)
2 0x8d9502df (0x8d912221)
##########:~/.wine[/email][/email]/drive_c/Program_Files/Namo/WebEditor_2006/bin$


whoah, could someone just shoot me?

---

### Post by grtwhiterhyno on 2009-05-21
bump

---

### Post by grtwhiterhyno on 2009-05-22
I have since solved this issue. here is what i did.


if you notice on lines 6 and 9 they start with fixme and then a name, which i learned usually is a dll name. in this case it was msimtf and imagehlp.

so i did some searching online to find these .dll files and downloaded them to my ~/.wine/drive_c/Windows/system32 folder.

after that i opened winecfg, or the wine configuration app,(Applications - Wine - Configure Wine) and on the libraries tab i added these dll files. they happened to be on the drop list which was helpful, but you could just as easily type them in if they are not in yours. make sure to click apply after adding each one. i left the setting at: native then builtin.

i also added the applications to the list found on the application tab. now whether this was necessary or not, i dont know, i did at first trying to fix it, and i havent tried removing and testing it. there you add the .exe file you want wine to handle and define the setting, or windows environment, you want to run your program in, ie: windows9*, XP, ME and so forth.

Hope this is helpful, and if i should be more specific or something let me know.

---

### Post by albinootje on 2009-05-22
> **grtwhiterhyno said:**
> I have since solved this issue. here is what i did.

if you notice on lines 6 and 9 they start with fixme and then a name, which i learned usually is a dll name. in this case it was msimtf and imagehlp.


Well done! :)

---

