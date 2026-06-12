---
title: "Problem in opening Ubuntu software center"
date: 2013-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shanasfish on 2013-02-24
I am using Dell Inspiron N5010 laptop. Whenever I am trying to run Ubuntu Software Center ,I am getting this message on the terminal
2013-02-24 22:34:14,645 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-02-24 22:34:14,650 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-02-24 22:34:14,978 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-02-24 22:34:15,183 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-02-24 22:34:15,621 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Segmentation fault (core dumped)
   I've also removed it and reinstalled it again but the same error message is showing.  What should I do?

---

### Post by gordintoronto on 2013-02-24
What version of Ubuntu are you using? Why are you trying to run software center from the terminal? What command did you enter?

---

### Post by shanasfish on 2013-02-25
I am using Ubuntu 12.04 . I am trying to open it from terminal window as well as from the launcher but every time its showing "Segmentation Fault(core dumped) ".

---

