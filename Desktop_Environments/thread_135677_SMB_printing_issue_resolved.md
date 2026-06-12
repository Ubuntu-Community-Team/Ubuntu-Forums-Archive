---
title: "SMB printing issue resolved"
date: 2006-02-24
forum: Desktop Environments
---

### Post by bosonflux on 2006-02-24
Posting this so others won't make same mistake.

I have been fighting to get SMB printing to a Windows 2000 shared printer for nearly 3 days working right. /var/log/cups/error_log kept telling me "could not connect to SMB host" NT_STATUS_BAD_NETWORK_NAME. I tried every URI string on these forums and the web and still always the same error. My problem was an invalid share name for the printer. I knew no spaces were allowed, but I have always used underbars (_) at times with no problems. My share name was Epson_r200. When I changed it to just r200, deleted the printer and used the standard Breezy printer setup, it worked perfectly the first test print. 

Hope this helps others in the future.

---

