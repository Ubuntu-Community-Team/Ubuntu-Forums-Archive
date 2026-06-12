---
title: "More of an email problem then an Ubuntu problem"
date: 2009-06-19
forum: General Help
---

### Post by supradave on 2009-06-19
I have a Cyrus IMAP server that I BCC every email to an archiving account.  Someone lost some email.  Any suggestions on how to get those messages back to the user in a functional format?  For example, we use encryption for internal email and if I do a 'mail -s subject user@fqdn < message', the message goes, but it's just text, none of the original functionality is there.  I have tried mutt and doing the set content_type, but the content type comes up in the original message as:

Content-Type: multipart/signed;
        protocol="application/x-pkcs7-signature";
        micalg=SHA1;
        boundary="----=_NextPart_000_00B4_01C9EE57.ED8C9A70"

So I tried mutt -e 'set content_type="multipart\/signed\;\ protocol=\"application\/x-pkcs7-signature\"\;\ micalg=SHA1\;\ boundary=\"----=_NextPart_000_00B4_01C9EE57.ED8C9A70\""' -s `grep ^Subject 120201. | cut -d\  -f2-` user@fqdn < 120201.

I have tried reformatting the above line also.

Thanks,
Dave

---

