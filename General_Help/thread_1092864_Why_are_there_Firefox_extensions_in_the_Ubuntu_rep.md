---
title: "Why are there Firefox extensions in the Ubuntu repositories?"
date: 2009-03-10
forum: General Help
---

### Post by Endolith on 2009-03-10
You can install Firefox extensions from Firefox itself.  There appears to be no connection between the extensions in Firefox and the ones in Synaptic.  Some are installed in one place and some in the other.  Why do these exist in the repositories?  Is the repository version better?

---

### Post by Tim Sharitt on 2009-03-10
The extensions installed via the repositories are installed to /usr/lib/firefox-addons where all user have access to them, but the extensions installed by a user via Firefox are installed to the users ~/.mozilla directory and are only accessible to that user.

Another difference is that the extensions in the repositories may not be completely up to date, except for possible security fixes.

---

### Post by Peasantoid on 2009-03-10
Hell, why not? :P

---

### Post by dcstar on 2009-03-10
> **Endolith said:**
> You can install Firefox extensions from Firefox itself.  There appears to be no connection between the extensions in Firefox and the ones in Synaptic.  Some are installed in one place and some in the other.  Why do these exist in the repositories?  Is the repository version better?

a) Convenience - instead of ploughing through thousands of Add-ons (that may be Windows only etc) some Linux and Ubuntu specific ones are made available in the repositories for easy access by Ubuntu users.

b) The Repository ones would have been tested so you know that they will work - if there are later updates then the Add-on itself should go looking for one after it has been installed.

---

