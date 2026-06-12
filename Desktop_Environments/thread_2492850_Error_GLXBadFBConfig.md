---
title: "Error GLXBadFBConfig"
date: 2023-11-24
forum: Desktop Environments
---

### Post by ubontik22 on 2023-11-24
Hello,

How to fix GLXBadFBConfig?
Thank you

```
$  blender -d --debug-all --log-level -1Switching to fully guarded memory allocator.
Blender 4.0.1
Build: 2023-11-17 00:31:26 Linux release
argv[0] = /snap/blender/4228/blender
argv[1] = -d
argv[2] = --debug-all
argv[3] = --log-level
argv[4] = -1
graph_id_tag_update: id=SCScene flags=BASE_FLAGS source=USER_EDIT
DEG_relations_tag_update: Tagging relations for update.
graph_id_tag_update: id=GRScene Collection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRCollection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GROVERRIDE_RESYNC_LEFTOVERS flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRScene Collection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRCollection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GROVERRIDE_RESYNC_LEFTOVERS flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRScene Collection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRCollection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GROVERRIDE_RESYNC_LEFTOVERS flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRScene Collection flags=TRANSFORM, GEOMETRY, COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=TRANSFORM, GEOMETRY, COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=TRANSFORM, GEOMETRY, COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRScene Collection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRCollection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GROVERRIDE_RESYNC_LEFTOVERS flags=COPY_ON_WRITE source=USER_EDIT
DEG_relations_tag_update: Tagging relations for update.
DEG_relations_tag_update: Tagging relations for update.
DEG_relations_tag_update: Tagging relations for update.
graph_id_tag_update: id=GRScene Collection flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=SCScene flags=COPY_ON_WRITE source=USER_EDIT
graph_id_tag_update: id=GRCollection flags=COPY_ON_WRITE source=USER_EDIT
Received X11 Error:
    error code:   167
    request code: 152
    minor code:   0
    error text:   GLXBadFBConfig
Received X11 Error:
    error code:   167
    request code: 152
    minor code:   0
    error text:   GLXBadFBConfig
Received X11 Error:
    error code:   167
    request code: 152
    minor code:   0
    error text:   GLXBadFBConfig
Received X11 Error:
    error code:   167
    request code: 152
    minor code:   0
    error text:   GLXBadFBConfig
Writing: /tmp/blender.crash.txt
Segmentation fault (core dumped)
```[COLOR=var(--hljs-string)][FONT=Consolas]
[/FONT][/COLOR]

---

