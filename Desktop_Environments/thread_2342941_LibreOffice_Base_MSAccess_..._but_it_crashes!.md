---
title: "LibreOffice Base: MSAccess ... but it crashes!"
date: 2016-11-11
forum: Desktop Environments
---

### Post by asearle on 2016-11-11
Dear Everyone,

For years I have been looking for an MS-Access replacement under Linux.  Open-/Libre-Office Base never quite "did it" for me.

But recently I started combining MySQL, PHPAdmin (via the browser) and Base (for ad-hoc viewing, editing and cut&paste) and now feel that I have found what I was looking for. I am VERY pleased.

However, while LibreOffice Write and Calc are pretty much rock-solid and rarely crash, Base seems to crash (lock up) regularly. And when it does, it brings Write and Calc down with it.  Arrgghh!!!

Can anyone help me with this?  How do I stop Base crashing?  If I could do that then I would be "over the moon" with the little combined environment that I have stumbled upon.

Regards and thanks,
Alan Searle
Cologne

---

### Post by QIII on 2016-11-11
Hello!

Could you start Base from the terminal and let us know if you get any messages when it crashes?

(By the way, I dispense with any control panels, Base and PHPMyAdmin and just use MySQL Workbench over SSH.  It has a pretty easy GUI interface.  If I want a more customized GUI application, I write one to open an SSH connection and a MySQL connection.)

Cheers.

---

### Post by asearle on 2016-11-11
Great: I'll try that and will give feedback.

The reason that I am using Base is that it provides copy-and-paste capability (backwards and forward to Calc) and ad-hoc filtering and sorting which is great for general data analysis.  This being possible both with tables and with SQL-Queries which can be stored and called up when needed.  This is great for getting to know a new database or for quick data entry.  Other (web-based) environments don't seem to offer this level of comfort (e.g. cut and paste).  

Also I would love to build Office-style database functionality (e.g. small-scale order-entry) that I could offer on all platforms (Windows, Mac and Linux) which LibreOffice could do.

I'm not putting down your choice of tools: Just explaining why Base would be a good "workhorse" for me (if I could make it stable).

Cheers,
Alan

---

### Post by SeijiSensei on 2016-11-11
I generally prefer Access because its GUI tools are better for complex select queries that rely on joins with multiple tables.  I have used Base with PostgreSQL as the back-end database and don't recall having any lockups.  Base comes with a native PG driver, while in Access I use the ODBC driver that Postgres distributes.  I've used Postgres for decades since MySQL was not open when I first began using databases on Linux.  I generally avoid MySQL and MariaDB as a result unless forced to use them as with WordPress.  Plus I find things like adding/deleting users and databases more clunky in MySQL; PG comes with command-line utilities for those types of tasks.

---

