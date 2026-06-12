---
title: "Missing Categories in Add/Remove"
date: 2009-02-14
forum: General Help
---

### Post by mhlz79 on 2009-02-14
Hello

When I click on Applications>Add/Remove, the window comes up but the list of categories down the left hand side is blank apart from 'All'

I'm using 8.10 on a Dell mini 9 (not using dell's version of ubuntu!)and the last changes I made were to install medibuntu repositories and BBC Iplayer desktop which comes with Adobe Air.

My repos look fine in System>Admin>Software Sources and Synaptic appears to be fine too. Any suggestions?

Thanks

Ben

---

### Post by drs305 on 2009-02-14
Try running this command to reinstall the add/remove app:
```

sudo apt-get install --reinstall app-install-data app-install-data-commercial

```

---

### Post by mhlz79 on 2009-02-14
wonderful! you are a complete legend!

Thank you.

Ben

---

