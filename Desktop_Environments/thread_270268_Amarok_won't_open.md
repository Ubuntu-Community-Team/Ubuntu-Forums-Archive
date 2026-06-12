---
title: "Amarok won't open"
date: 2006-10-03
forum: Desktop Environments
---

### Post by waltervalderrama on 2006-10-03
After typing amarok in a terminal, i get this. I see splash screen but after that it closes. What is happening, please help. I captured last lines before closing.


amarok:     [CollectionDB] [ERROR!] no such table: admin
amarok:     [CollectionDB] [ERROR!] on query: SELECT value FROM admin WHERE noption = 'Database Stats Version';
amarok:     [CollectionDB] [ERROR!] Database statistics version too new for this version of Amarok. Quitting...
amarok: BEGIN: virtual CollectionDB::~CollectionDB()
amarok:       [CollectionDB] Running VACUUM
amarok: END__: virtual CollectionDB::~CollectionDB() - Took 1.9s
amarok:     [virtual EngineController::~EngineController()] 
DCOP: unregister 'amarok'

---

### Post by wieman01 on 2006-10-03
Mmm... Have you uninstalled MySQL or any other database recently? I think Amarok is using a database for playlists, etc. and can't find it:
> SELECT value FROM admin WHERE noption = 'Database Stats Version';

---

