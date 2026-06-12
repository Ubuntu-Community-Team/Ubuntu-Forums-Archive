---
title: "Mime types : how to hande force-download or x-download types?"
date: 2009-03-20
forum: General Help
---

### Post by josce on 2009-03-20
Some mail clients use mime-types such as
 Content-Type: application/x-download;
or
 Content-Type: application/force-download;
regardless of the actual filetype. 

When receiving such an attachment, the mime resolution (at leat in mutt) does not work. Is there a way to override the mime description in the message received ? 

Alternatively I'd define a mime type entry for these types, use "file" to get the actual mime-type, and run the right viewing command from mailcap: 
is there a linux command which resolves the mailcap entry from the mime type or do I have to write this myself ?

Best wishes,
Jocelyn

---

### Post by josce on 2009-03-20
Well, josce, says josce, rtFm :

in mutt, use the following commands in your muttrc :
 mime_lookup application/force-download
 mime_lookup application/x-download

Best wishes, josce. Happy to be of some help.

---

