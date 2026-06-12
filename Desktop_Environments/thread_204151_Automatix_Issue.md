---
title: "Automatix Issue"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Mike_N on 2006-06-26
I got Automatix and it was doing fine and then i got this...

W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures were invalid: BADSIG 18B52FE3521A9C7C Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>
W: You may want to run apt-get update to correct these problems


... I had something similar with Breezy that was corrected by one simple command, any ideas?

Thanks, Mike

---

### Post by stengah on 2006-06-26
Same error her... any ideas?

---

### Post by angkor on 2006-06-26
Try this:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

Edit: hmm, guess not, that just adds the key if you don't have one. I need to read posts better.

seems people are looking into it.

[http://ubuntuforums.org/showpost.php?p=1182959&postcount=6](http://ubuntuforums.org/showpost.php?p=1182959&postcount=6)

---

### Post by Mike_N on 2006-06-26
Just found this, wasn't too sure but tried it anyway and it worked...

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

... However, if anyone can tell me the difference between this and the suggestion posted above, it would be appreciated... Mike

---

