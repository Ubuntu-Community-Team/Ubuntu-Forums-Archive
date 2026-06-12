---
title: "Problem with lftp to server running Pure-FTPd"
date: 2006-07-07
forum: Desktop Environments
---

### Post by slider on 2006-07-07
I'm trying to lftp to my server hosted on Lunarpages from my Ubuntu 6.06 desktop machine. The server is running PureFTPd.

It logs in fine, cd and pwd work fine. ls or put cause a hang and I get dropped. 

Working with the same server, regular ftp works fine, lftp 3.1 on my Mac0SX laptop works fine and so does CoreFTP running in XP hosted in VMWare on the same machine. lftp works fine to other ftp servers from my Ubuntu box, this is the only server I've run into so far that hangs. I have tried turning off passive mode with:

"set ftp: passive-mode off"

which did not help. In fact part of the strangeness is that it still falls back to passive mode and hangs even after setting passive-mode off. Here's the tail of the log file right before it hangs.

Any help would be appreciated.

<--- 250 OK. Current directory is /www/transfer
GNUTLS: ASSERT: gnutls_buffers.c:255

......

GNUTLS: ASSERT: gnutls_buffers.c:255
---> PROT P

GNUTLS: REC[836a9f8]: Sending Packet[7] Application Data(23) with length: 8
GNUTLS: REC[836a9f8]: Sent Packet[8] Application Data(23) with length: 261
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: REC[836a9f8]: Expected Packet[8] Application Data(23) with length: 65536
GNUTLS: REC[836a9f8]: Received Packet[8] Application Data(23) with length: 48
GNUTLS: REC[836a9f8]: Decrypted Packet[8] Application Data(23) with length: 21
<--- 534 Fallback to [C]
---> PASV

GNUTLS: REC[836a9f8]: Sending Packet[8] Application Data(23) with length: 6
GNUTLS: REC[836a9f8]: Sent Packet[9] Application Data(23) with length: 197
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: REC[836a9f8]: Expected Packet[9] Application Data(23) with length: 65536
GNUTLS: REC[836a9f8]: Received Packet[9] Application Data(23) with length: 80
GNUTLS: REC[836a9f8]: Decrypted Packet[9] Application Data(23) with length: 53
<--- 227 Entering Passive Mode (xxx,xxx,xxx,xxx,252,215)
---- Connecting data socket to (xxx.xxx.xxx.xxx) port 64727
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255
GNUTLS: ASSERT: gnutls_buffers.c:255

---

