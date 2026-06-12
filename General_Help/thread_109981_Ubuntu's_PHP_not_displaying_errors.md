---
title: "Ubuntu's PHP not displaying errors"
date: 2005-12-29
forum: General Help
---

### Post by guice on 2005-12-29
I've created a small test script with: ```
<? phpinfo(); junk(); ?>
```expecting to see an undefined function error at the bottom of the page; however, there's nothing. I have display_errors turned on and junk() definatly isn't a valid PHP function...

What did Ubuntu's PHP install do differently to stop this from working properly? How can I fix it?

PS: I've moved the URL. Already got hackers trying to break into my Apache server. /sigh

---

### Post by guice on 2005-12-29
Well, I found out it's related to E_STRICT although E_STRICT isn't suppose to supress error messages...

---

