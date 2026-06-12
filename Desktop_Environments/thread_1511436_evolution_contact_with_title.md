---
title: "evolution contact with title"
date: 2010-06-16
forum: Desktop Environments
---

### Post by mathfeel on 2010-06-16
I have noticed a strange problem with evolution. I am using Lucid.

If I have a contact with title, say
```
Dr. John Smith <jsmith@host.com>
```

When I use address completion during composing a message, then the above string will go into the "To" field. Nothing strange.

However, when I send the email out (using Gmail smtp), it will bounce back as undeliverable. A closer inspection of the error says:
```
The following message to <mith jsmith@host.com> was undeliverable
```

Now, if I try again but remove the "Dr.<space>" part manually before I click send, the email is delivered. Actually I just realized that removing the period also works. I hypothesize that evolution is treating the title that ends in a period as the middle initial. Is this a bug in evolution?

--
MZ

---

