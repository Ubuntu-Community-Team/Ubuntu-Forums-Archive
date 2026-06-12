---
title: "Compiz issue Ubuntu 12.04"
date: 2013-05-28
forum: Desktop Environments
---

### Post by bturrie on 2013-05-28
Starting at the beginning, dash couldn't find any applications so I did:

rm ~/.cache/software-center -R
unity --reset &

Lots of out put at that point, the most concerning was this:

(compiz:9067): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000aa!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000ad!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000b0!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2a000b3!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.

(compiz:9067): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

I tried filing a bug report with 

unity-bug compiz

but the program said a bug could not be filed until I went through proper channels since precise was no longer under development.

So, I'm not sure how to proceed. Not sure what an unhandled configurenotify is or whether I should care. Any thoughts?

Dash is working properly now btw.

---

