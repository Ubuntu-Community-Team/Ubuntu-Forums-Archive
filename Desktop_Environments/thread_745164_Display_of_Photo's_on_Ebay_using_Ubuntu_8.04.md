---
title: "Display of Photo's on Ebay using Ubuntu 8.04"
date: 2008-04-04
forum: Desktop Environments
---

### Post by rweddell on 2008-04-04
Urgent needs to be addressed before final release !!!!

I am using Ubuntu 8.04 bata version. 
Problem is that I can't see (only) my ebay photos, in my auctions.
Reverted back to Ubuntu 7.10 and all picture showed up.

1. <a HREF=http://storage.red-ring.com/users/hobnail/auctions/P0006644.jpg> (displays OK)

2. <img BORDER=1 SRC=http://storage.red-ring.com/users/hobnail/auctions/P0006645.jpg
width=300 height=200><font SIZE=1><br>Pictures Hosted by Red-Wing Software -- Click image to view larger version</font></a><br><br>                                                               (does not display)

Using Ubuntu 7.10 this code works fine.  Could someone please help me with this. I suppose that this is a common problem and may just need a little tweak to correct  in the Ubuntu version 8.04.

Please get up with me if I can give you any other information that you may need to resolve this issue.

---

### Post by richiewrt on 2008-04-04
not sure about ebay, but in html, your attributes need **""**,  example:
1.  <a HREF="http://storage.red-ring.com/users/hobnail/auctions/P0006644.jpg">

2. <img BORDER="1"" SRC="http://storage.red-ring.com/users/hobnail/auctions/P0006645.jpg"
width="300" height="200"><font SIZE="1"><br>Pictures Hosted by Red-Wing Software -- Click image to view larger version</font></a><br><br>

You can try that and see if it helps.  Not very well formed html though.

---

