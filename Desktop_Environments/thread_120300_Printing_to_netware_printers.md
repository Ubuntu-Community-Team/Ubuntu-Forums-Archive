---
title: "Printing to netware printers"
date: 2006-01-21
forum: Desktop Environments
---

### Post by mendred on 2006-01-21
Hi I would like to know how to set up netware printers that use the IPX protocol in kde. Presently i use the ncpfs tools (ipx-configure, nprint, pqlist to access the printer from the command line) and they detect the printer just fine.

After running
sudo ipx_configure --auto_interface=on --auto_primary=on

output of  slist

Known NetWare File Servers                          Network   Node Address
--------------------------------------------------------------------------
PRINT                                               3862809C  000000000001

output of pqlist:

Server: PRINT
Print queue name                                    Queue ID
------------------------------------------------------------
MH                                                  BA000001
LHREDIRECT                                          BB000001
LIBREDIR                                            BC000001
LHCOLOR                                             BD000001
LH                                                  BE000001
COLOR                                               BF000001
URGENT                                              C0000001
LIB                                                 C1000001
GH3                                                 E8020001


I tried playing with kde's printer tools, doesn't seem to have an option for IPX (Atleast couldn't find any)

Any help would be appreciated. Thanks in advance

Bharat

---

### Post by mjh007 on 2006-04-24
HI Bharat

I stumbled across your post when I was searching for the answer to my similar problem. I'm using Ubuntu Dapper and couldn't get my printing to a Netware printer working either.

I managed to use the nprint command from the ncpfs package, but that resulted in the "staircase effect" due to the lack of the proper driver/filter. I then tried all the different printing tools from the default CUPS to lpd, lpr, lprng but was unsuccessful. 

Eventually I came across the package "printtool" which is the Red Hat printing package, which has the option of printing to a Netware printer. It solved my problem and I could use the correct driver for the printer and so there was no "staircase effect" anymore.

I hope this helps you too.

---

