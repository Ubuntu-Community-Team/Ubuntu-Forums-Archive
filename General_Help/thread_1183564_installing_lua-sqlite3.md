---
title: "installing lua-sqlite3"
date: 2009-06-10
forum: General Help
---

### Post by lyzby on 2009-06-10
I'm trying to get lua-sqlite3 to work.  I installed Lua 5.1.4 and sqlite3 using apt-get, and lua-sqlite3 by wgetting, untarring, configuring and making lua-sqlite3-0.4.1.tar.gz.  Everything, including my own program, works fine when run from /usr/src/lua-sqlite3-0.4.1/examples.

When I run from somewhere else, say /home/me/lua, I get the following messages:

```

lua: simple.lua:3: module 'sqlite3' not found:
        no field package.preload['sqlite3']
        no file 'sqlite3'
        no file 'sqlite3.lua'
        no file '../sqlite3'
        no file '../sqlite3.lua'
        no file './sqlite3.so'
        no file '/usr/local/lib/lua/5.1/sqlite3.so'
        no file '/usr/local/lib/lua/5.1/loadall.so'
stack traceback:
        [C]: in function 'require'
        simple.lua:3: in main chunk
        [C]: ?

```

This is with the example file, "simple.lua":

```

require "path"
require "sqlite3"


local db = sqlite3.open_memory()

db:exec[[
  CREATE TABLE test (id INTEGER PRIMARY KEY, content);

  INSERT INTO test VALUES (NULL, 'Hello World');
  INSERT INTO test VALUES (NULL, 'Hello Lua');
  INSERT INTO test VALUES (NULL, 'Hello Sqlite3')
]]

for row in db:rows("SELECT * FROM test") do
  print(row.id, row.content)
end

```

What do I need to do to make it so that lua can find the necessary sqlite3 files?

---

