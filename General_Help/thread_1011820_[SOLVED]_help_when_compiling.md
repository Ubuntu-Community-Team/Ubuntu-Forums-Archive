---
title: "[SOLVED] help when compiling"
date: 2008-12-15
forum: General Help
---

### Post by djbushido on 2008-12-15
okay, first, sorry for the generic heading.
I'm trying to compile qosmic for linux (already have flam3 compiled) and i keep on getting this error that i don't know what to do with:
```
luathread.cpp:(.text._ZN3Lua5LunarINS_5FrameEE5thunkEP9lua_State[Lua::Lunar<Lua::Frame>::thunk(lua_State*)]+0xac): undefined reference to `luaL_error'
luathread.cpp:(.text._ZN3Lua5LunarINS_5FrameEE5thunkEP9lua_State[Lua::Lunar<Lua::Frame>::thunk(lua_State*)]+0xcc): undefined reference to `luaL_typerror'
collect2: ld returned 1 exit status
make: *** [qosmic] Error 1
error while building qosmic

```

note that there were more "lua" references above this, i can post the entire log if someone needs it, but it is fairly long.

I don't know how to fix this error (maybe update lua? again how?), any help would be appreciated.

---

### Post by djbushido on 2008-12-16
Okay, so i just installed qosmic from ultimate edition repo's, that works.

---

