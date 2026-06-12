---
title: "Ubuntu 13.10 devilspie settings"
date: 2014-03-23
forum: Desktop Environments
---

### Post by nibal on 2014-03-23
In Ubuntu 13.10, desktop workspaces are declared in System settings, and not with ccsm. As such, system will create a 2x2 desktop environment. With the following configuration I manage to arrange windows in the first row, but nothing in the second.A 2x2 desktop, is already limited, i would like to at least be able the use additional row. Anyone knows how to do it?

```

(if (is (application_name) "Opera")
      (begin (set_viewport 2)
                       (maximize)
     )
)

(if (is (application_name) "qBittorrent v2.9.7")
       (begin (set_viewport 4)
      )
)

(if (is (application_name) "Clementine")
      (begin (set_viewport 3)
      )
)

(if (is (application_name) "Terminal")
    (begin (set_viewport 1)
          (if (is (window_role) "1")
                  (begin (geometry "750x1000+0+0")
                  )
          )
          (if (is (window_role) "2")
                  (begin (geometry "750x1000+750+0")
                  )
          )
          (if (is (window_role) "3")
                   (begin (geometry "750x1000+950+0")
                   )
          )
    )
)

```

---

