---
title: "Thunderbird Locks Up Or Closes"
date: 2009-06-13
forum: General Help
---

### Post by jlabomb on 2009-06-13
Recently Thunderbird has been locking up and turning grey till I have to use the system monitor to close it or it will just close on its own. I ran it out of the terminal and pasted it below. I didn't make any changes that I know of. Any help would be appreciated.


> james@james-desktop:~$ thunderbird
*** glibc detected *** /usr/lib/thunderbird/thunderbird-bin: double free or corruption (out): 0x00007fdaccc426e0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fdada8e7cb8]
/lib/libc.so.6(cfree+0x76)[0x7fdada8ea276]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec5b8ef]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec5e3fb]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec3f1b7]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec3fae9]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec8968f]
/usr/lib/thunderbird/libmozjs.so(JS_NewStringCopyZ+0x79)[0x7fdadec14789]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec63c58]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec642f9]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec5a32a]
/usr/lib/thunderbird/libmozjs.so[0x7fdadec4c0a8]
/usr/lib/thunderbird/libmozjs.so(js_Invoke+0xba2)[0x7fdadec42c62]
/usr/lib/thunderbird/components/libxpconnect.so[0x7fdad4b3e274]
/usr/lib/thunderbird/libxpcom_core.so[0x7fdade7b9016]
/usr/lib/thunderbird/libxpcom_core.so[0x7fdade7b84ab]
======= Memory map: ========
00400000-00415000 r-xp 00000000 08:01 278950                             /usr/lib/thunderbird/thunderbird-bin
00615000-00616000 r--p 00015000 08:01 278950                             /usr/lib/thunderbird/thunderbird-bin
00616000-00617000 rw-p 00016000 08:01 278950                             /usr/lib/thunderbird/thunderbird-bin
00b30000-01c66000 rw-p 00b30000 00:00 0                                  [heap]
7fdabf7e8000-7fdabf808000 r-xp 00000000 08:01 278925                     /usr/lib/thunderbird/components/libwallet.so
7fdabf808000-7fdabfa07000 ---p 00020000 08:01 278925                     /usr/lib/thunderbird/components/libwallet.so
7fdabfa07000-7fdabfa08000 r--p 0001f000 08:01 278925                     /usr/lib/thunderbird/components/libwallet.so
7fdabfa08000-7fdabfa09000 rw-p 00020000 08:01 278925                     /usr/lib/thunderbird/components/libwallet.so
7fdabfa09000-7fdabfa0a000 ---p 7fdabfa09000 00:00 0 
7fdabfa0a000-7fdac020a000 rw-p 7fdabfa0a000 00:00 0 
7fdac020a000-7fdac020b000 ---p 7fdac020a000 00:00 0 
7fdac020b000-7fdac0a0b000 rw-p 7fdac020b000 00:00 0 
7fdac0a0b000-7fdac0a0c000 ---p 7fdac0a0b000 00:00 0 
7fdac0a0c000-7fdac120c000 rw-p 7fdac0a0c000 00:00 0 
7fdac120c000-7fdac1213000 r-xp 00000000 08:01 278734                     /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fdac1213000-7fdac1413000 ---p 00007000 08:01 278734                     /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fdac1413000-7fdac1414000 r--p 00007000 08:01 278734                     /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fdac1414000-7fdac1415000 rw-p 00008000 08:01 278734                     /usr/lib/thunderbird/components/libxpcom_compat_c.so
7fdac1415000-7fdac141a000 r-xp 00000000 08:01 312857                     /lib/libnss_dns-2.9.so
7fdac141a000-7fdac1619000 ---p 00005000 08:01 312857                     /lib/libnss_dns-2.9.so
7fdac1619000-7fdac161a000 r--p 00004000 08:01 312857                     /lib/libnss_dns-2.9.so
7fdac161a000-7fdac161b000 rw-p 00005000 08:01 312857                     /lib/libnss_dns-2.9.so
7fdac161b000-7fdac161d000 r-xp 00000000 08:01 114                        /lib/libnss_mdns4_minimal.so.2
7fdac161d000-7fdac181c000 ---p 00002000 08:01 114                        /lib/libnss_mdns4_minimal.so.2
7fdac181c000-7fdac181d000 rw-p 00001000 08:01 114                        /lib/libnss_mdns4_minimal.so.2
7fdac181d000-7fdac181e000 ---p 7fdac181d000 00:00 0 
7fdac181e000-7fdac201e000 rw-p 7fdac181e000 00:00 0 
7fdac201e000-7fdac209e000 r--p 00000000 08:01 35098                      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
7fdac209e000-7fdac20a6000 r-xp 00000000 08:01 278922                     /usr/lib/thunderbird/components/libmsgsmime.so
7fdac20a6000-7fdac22a5000 ---p 00008000 08:01 278922                     /usr/lib/thunderbird/components/libmsgsmime.so
7fdac22a5000-7fdac22a6000 r--p 00007000 08:01 278922                     /usr/lib/thunderbird/components/libmsgsmime.so
7fdac22a6000-7fdac22a7000 rw-p 00008000 08:01 278922                     /usr/lib/thunderbird/components/libmsgsmime.so
7fdac22a7000-7fdac22bd000 r-xp 00000000 08:01 278947                     /usr/lib/thunderbird/components/libmailcomps.so
7fdac22bd000-7fdac24bd000 ---p 00016000 08:01 278947                     /usr/lib/thunderbird/components/libmailcomps.so
7fdac24bd000-7fdac24be000 r--p 00016000 08:01 278947                     /usr/lib/thunderbird/components/libmailcomps.so
7fdac24be000-7fdac24bf000 rw-p 00017000 08:01 278947                     /usr/lib/thunderbird/components/libmailcomps.so
7fdac24bf000-7fdac2519000 r-xp 00000000 08:01 802891                     /usr/lib/nss/libnssckbi.so
7fdac2519000-7fdac2718000 ---p 0005a000 08:01 802891                     /usr/lib/nss/libnssckbi.so
7fdac2718000-7fdac2726000 r--p 00059000 08:01 802891                     /usr/lib/nss/libnssckbi.so
7fdac2726000-^C


---

### Post by jlabomb on 2009-06-21
No help?

---

