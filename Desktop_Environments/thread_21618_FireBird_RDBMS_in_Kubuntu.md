---
title: "FireBird RDBMS in Kubuntu"
date: 2005-03-23
forum: Desktop Environments
---

### Post by freex on 2005-03-23
i've just installed a fresh Kubuntu in my box. And am very happy with it, and looking forward for the stable version on april.

I just want to ask, is there a thread/link where i can find a "How to" install FireBird 1.5.X on Kubuntu. i know it sounds dumb but i am really new to this, i just want to get out of the MS paradigm and move on the lighter-side of the force  :smile:

---

### Post by maurom on 2005-04-15
Firebird can be installed by following these steps:

1. Enable universe repository (see [www.ubuntuguide.org](www.ubuntuguide.org))
2. $ apt-get install firebird2-classic-server (or firebird2-super-server, according to your needs, see Firebird web)
3. $ apt-get install firebird2-utils-classic

Then you can use the isql-fb app to create/connect to a database and execute SQL queries.

If you need php4 support, execute
4. $ apt-get install php4-interbase

See [www.firebirdsql.org](www.firebirdsql.org) for tutorials and documentation.

---

