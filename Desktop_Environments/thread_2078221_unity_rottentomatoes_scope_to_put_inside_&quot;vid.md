---
title: "unity: rottentomatoes scope to put inside &quot;videos&quot; lens"
date: 2012-10-30
forum: Desktop Environments
---

### Post by PhartSmellah on 2012-10-30
Hello all,

I'm using Ubuntu 12.10 64-bit with Unity.
I've recently installed a few lenses, on top of the ones that ship with the distro. I also installed the rottentomatoes scope (**unity-scope-torrentomatoes**) from scope-packagers.

Thing is - rottentomatoes shows its query results in the main (global) lens, and I want it to reside in the "videos" lens. I belive this is because there was an update to the videos lens from 11.10 to 12.10, and rottentomatoes scope has yet to be updated.

I've done the following:
1. In **/usr/lib/unity-scope-rottentomatoes/unity-scope-rottentomatoes**:
```

[COLOR="Red"]BUS_NAME = "net.launchpad.scope.videos.rottentomatoes"[/COLOR]

class Daemon:

    def __init__ (self):
        # The path for the Lens *must* also match the one in our .lens file
[COLOR="red"]        self.scope = Unity.Scope.new ("/net/launchpad/scope/videos/rottentomatoes")[/COLOR]
[COLOR="Red"]        self.scope.search_in_global = False[/COLOR]
        self.scope.connect("search-changed", self.on_search_changed)
        svg_dir = "/usr/share/icons/unity-icon-theme/places/svg/"
        self.scope.export()
        print "babar"

    def on_search_changed (self, scope, search, search_type, *_):
        ....
        ....
```

2. In **/usr/share/dbus-1/services/unity-scope-rottentomatoes.service**
```
[D-BUS Service]
Name=net.launchpad.scope.videos.rottentomatoes
Exec=/usr/lib/unity-scope-rottentomatoes/unity-scope-rottentomatoes
```

3. Deleted **/usr/share/unity/lenses/utilities/rottentomatoes.scope**

4. Added **/usr/share/unity/lenses/video/rottentomatoes.scope**:
```
[Scope]
DBusName=net.launchpad.scope.videos.rottentomatoes
DBusPath=/net/launchpad/scope/videos/rottentomatoes
```

And it still doesn't show up in "videos" lens...
What's more annoying - it still shows up in the global search!! (even though I disable search_in_global) ](*,)
What's missing??

---

### Post by PhartSmellah on 2012-11-03
bump...
really? no one?

---

### Post by PhartSmellah on 2012-11-14
bump

---

### Post by PhartSmellah on 2013-01-07
Bump

---

