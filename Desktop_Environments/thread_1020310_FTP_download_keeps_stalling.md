---
title: "FTP download keeps stalling"
date: 2008-12-24
forum: Desktop Environments
---

### Post by nizdobs on 2008-12-24
I'm committed to flipping the switch away from Windows for good so I installed Ubuntu on my laptop. I work for a small software company and our software runs on Linux so the first thing I sought to do was to get our software installed on my laptop. I went to download the files from our ftp server and the download stalled repeatedly despite my trying numerous ftp clients including: gFTP, KFTPGrabber, terminal window, and Firefox. In gFTP and KFTPGrabber I could see very brief bursts of download activity followed by long periods of inactivity. 

I thought the problem might be with the ftp server so I brought up a windows box and pulled the file down without any problem using a windows ftp client.

Can anyone give me some insight about why I'd be having trouble pulling this file down?

Thanks,

- Niz

---

### Post by thegnark on 2008-12-24
I can't think of anything that would inherently be limiting you, but have you troubleshooted various hardware aspects? i.e. network port, cabling, NIC card

Can you download large files via other methods such as HTTP? What about SFTP?

---

### Post by nizdobs on 2008-12-24
Looks like the problem has gone away. The only difference I can think of is this: Earlier tonight I added the Firestarter firewall from Synaptic but had not yet configured it. That's when the downloads kept stalling. Once I had started and configured Firestarter the download ran fine.

Does that make any sense or must there be some other explanation?

Thanks for the assistance.

- Niz

---

