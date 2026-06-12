---
title: "Rsync Destroys System"
date: 2008-05-05
forum: Desktop Environments
---

### Post by RPG405 on 2008-05-05
Here's the story. I upgraded from 7.10 (or whatever the previous version of Ubuntu was - I'm not very good with numbers) to 8.04 using the upgrade manager. On 7.10, I used to make weekly backups of my /home/ directory with rsync. The command is listed below:
```
rsync -rvu --delete --progress --stats --exclude=".thumbnails" ~/ /media/sdc1/garrett
```
It's worked wonderfully for me. Now, the first time I tried to do this on 8.04, I was busy doing other tasks. During it's backup run, it suddenly froze the system. This is a bad freeze, which could not be gotten out of by ANY means at all. Everything on the screen was frozen, no mouse, no keyboard, could not switch to another shell CTRL + ALT + (F1 - F6) could NOT EVEN USE THE SysRq key to reboot the system! (Alt + Prt Scr + R + E + I + S + U + B, for those of you who want to know).

Thinking it was a conflict of interest between programs, I tried running it again with me monitoring the terminal the entire time. This time it froze the system while moving a ~2MB image file from my /home/ directory to my backup disk. Okay, I thought, I hard-rebooted the system again (involving cussing and pulling out power cords until I got the right one), deleted the file, and tried it once again. Again, it froze during the transfer of (ironically enough) the Ubuntu 8.04 ISO file (which I had downloaded for my other computer). Full system lock and the only way out of it was more cussing and cord-pulling.

That's enough of using rsync, and I'm using Ubuntu 8.04 now with no worries. Whenever I pull up rsync, though, it'll crash into a pit of smoldering embers.

The hard drive I back the data up to is an external drive connected via USB 2.0 cable. It seems like the kernel is panacking, maybe something with the USB io modules, but with no way to recover from it, it's hard to pin down a source for the beast.

Help if you can.

---

### Post by p_quarles on 2008-05-05
Try running your rsync command with the "-n" or "--dry-run" option enabled (they both mean the same thing). This will run a simulation of the operation without actually transferring any files. Along with the -v option, it may give you a hint about where the problem lies.

---

### Post by RPG405 on 2008-05-06
The output of this:
```
 rsync -rvnu --delete --progress --stats --exclude=".thumbnails" ~/ /media/sdc1/garrett
```

is this:

(some lines truncated for display)
```
building file list ... 
62924 files to consider
IO error encountered -- skipping file deletion
skipping non-regular file ".DCOPserver_garrett-desktop_:0"
.DCOPserver_garrett-desktop__0
.ICEauthority
.Xauthority
.bash_history
.dmrc
.gksu.lock
.recently-used
.recently-used.xbel
.tomboy.log
.xsession-errors
skipping non-regular file "googleearth"
rsync_dry_run.txt
rsyncout.txt
skipping non-regular file ".blender/.Blanguages"
skipping non-regular file ".blender/.bfont.ttf"
skipping non-regular file ".blender/locale"
skipping non-regular file ".blender/scripts/3ds_export.py"
skipping non-regular file ".blender/scripts/3ds_export.pyc"
skipping non-regular file ".blender/scripts/3ds_import.py"
skipping non-regular file ".blender/scripts/3ds_import.pyc"
skipping non-regular file ".blender/scripts/Axiscopy.py"
skipping non-regular file ".blender/scripts/Axiscopy.pyc"
skipping non-regular file ".blender/scripts/DirectX8Exporter.py"
skipping non-regular file ".blender/scripts/DirectX8Exporter.pyc"
skipping non-regular file ".blender/scripts/DirectX8Importer.py"
skipping non-regular file ".blender/scripts/DirectX8Importer.pyc"
skipping non-regular file ".blender/scripts/IDPropBrowser.py"
skipping non-regular file ".blender/scripts/IDPropBrowser.pyc"
skipping non-regular file ".blender/scripts/ac3d_export.py"
skipping non-regular file ".blender/scripts/ac3d_export.pyc"
skipping non-regular file ".blender/scripts/ac3d_import.py"
skipping non-regular file ".blender/scripts/ac3d_import.pyc"
skipping non-regular file ".blender/scripts/add_mesh_torus.py"
skipping non-regular file ".blender/scripts/add_mesh_torus.pyc"
skipping non-regular file ".blender/scripts/animation_trajectory.py"
skipping non-regular file ".blender/scripts/animation_trajectory.pyc"
skipping non-regular file ".blender/scripts/armature_symetry.py"
skipping non-regular file ".blender/scripts/armature_symetry.pyc"
skipping non-regular file ".blender/scripts/armature_symmetry.py"
skipping non-regular file ".blender/scripts/armature_symmetry.pyc"
skipping non-regular file ".blender/scripts/bevel_center.py"
skipping non-regular file ".blender/scripts/bevel_center.pyc"
skipping non-regular file ".blender/scripts/blender2cal3d.py"
skipping non-regular file ".blender/scripts/blender2cal3d.pyc"
skipping non-regular file ".blender/scripts/blenderLipSynchro.py"
skipping non-regular file ".blender/scripts/blenderLipSynchro.pyc"
skipping non-regular file ".blender/scripts/bpydata"
skipping non-regular file ".blender/scripts/bpymodules"
skipping non-regular file ".blender/scripts/bvh2arm.py"
skipping non-regular file ".blender/scripts/bvh2arm.pyc"
skipping non-regular file ".blender/scripts/bvh_import.py"
skipping non-regular file ".blender/scripts/bvh_import.pyc"
skipping non-regular file ".blender/scripts/camera_changer.py"
skipping non-regular file ".blender/scripts/camera_changer.pyc"
skipping non-regular file ".blender/scripts/colladaExport14.py"
skipping non-regular file ".blender/scripts/colladaExport14.pyc"
skipping non-regular file ".blender/scripts/colladaImEx"
skipping non-regular file ".blender/scripts/colladaImport14.py"
skipping non-regular file ".blender/scripts/colladaImport14.pyc"
skipping non-regular file ".blender/scripts/collada_export.py"
skipping non-regular file ".blender/scripts/collada_export.pyc"
skipping non-regular file ".blender/scripts/collada_import.py"
skipping non-regular file ".blender/scripts/collada_import.pyc"
skipping non-regular file ".blender/scripts/config.py"
skipping non-regular file ".blender/scripts/config.pyc"
skipping non-regular file ".blender/scripts/console.py"
skipping non-regular file ".blender/scripts/console.pyc"
skipping non-regular file ".blender/scripts/discombobulator.py"
skipping non-regular file ".blender/scripts/discombobulator.pyc"
skipping non-regular file ".blender/scripts/disp_paint.py"
skipping non-regular file ".blender/scripts/disp_paint.pyc"
skipping non-regular file ".blender/scripts/doc_browser.py"
skipping non-regular file ".blender/scripts/doc_browser.pyc"
skipping non-regular file ".blender/scripts/envelope_assignment.py"
skipping non-regular file ".blender/scripts/envelope_assignment.pyc"
skipping non-regular file ".blender/scripts/envelope_symmetry.py"
skipping non-regular file ".blender/scripts/envelope_symmetry.pyc"
skipping non-regular file ".blender/scripts/export-iv-0.1.py"
skipping non-regular file ".blender/scripts/export-iv-0.1.pyc"
skipping non-regular file ".blender/scripts/export_cal3d.py"
skipping non-regular file ".blender/scripts/export_cal3d.pyc"
skipping non-regular file ".blender/scripts/export_fbx.py"
skipping non-regular file ".blender/scripts/export_fbx.pyc"
skipping non-regular file ".blender/scripts/export_lightwave_motion.py"
skipping non-regular file ".blender/scripts/export_lightwave_motion.pyc"
skipping non-regular file ".blender/scripts/export_map.py"
skipping non-regular file ".blender/scripts/export_map.pyc"
skipping non-regular file ".blender/scripts/export_mdd.py"
skipping non-regular file ".blender/scripts/export_mdd.pyc"
skipping non-regular file ".blender/scripts/export_obj.py"
skipping non-regular file ".blender/scripts/export_obj.pyc"
skipping non-regular file ".blender/scripts/faceselect_same_weights.py"
skipping non-regular file ".blender/scripts/faceselect_same_weights.pyc"
skipping non-regular file ".blender/scripts/flt_export.py"
skipping non-regular file ".blender/scripts/flt_export.pyc"
skipping non-regular file ".blender/scripts/flt_filewalker.py"
skipping non-regular file ".blender/scripts/flt_filewalker.pyc"
skipping non-regular file ".blender/scripts/flt_import.py"
skipping non-regular file ".blender/scripts/flt_import.pyc"
skipping non-regular file ".blender/scripts/help_bpy_api.py"
skipping non-regular file ".blender/scripts/help_bpy_api.pyc"
skipping non-regular file ".blender/scripts/help_browser.py"
skipping non-regular file ".blender/scripts/help_browser.pyc"
skipping non-regular file ".blender/scripts/help_getting_started.py"
skipping non-regular file ".blender/scripts/help_getting_started.pyc"
skipping non-regular file ".blender/scripts/help_manual.py"
skipping non-regular file ".blender/scripts/help_manual.pyc"
skipping non-regular file ".blender/scripts/help_py_reference.py"
skipping non-regular file ".blender/scripts/help_py_reference.pyc"
skipping non-regular file ".blender/scripts/help_release_notes.py"
skipping non-regular file ".blender/scripts/help_release_notes.pyc"
skipping non-regular file ".blender/scripts/help_tutorials.py"
skipping non-regular file ".blender/scripts/help_tutorials.pyc"
skipping non-regular file ".blender/scripts/help_web_blender.py"
skipping non-regular file ".blender/scripts/help_web_blender.pyc"
skipping non-regular file ".blender/scripts/help_web_devcomm.py"
skipping non-regular file ".blender/scripts/help_web_devcomm.pyc"
skipping non-regular file ".blender/scripts/help_web_eshop.py"
skipping non-regular file ".blender/scripts/help_web_eshop.pyc"
skipping non-regular file ".blender/scripts/help_web_usercomm.py"
skipping non-regular file ".blender/scripts/help_web_usercomm.pyc"
skipping non-regular file ".blender/scripts/hotkeys.py"
skipping non-regular file ".blender/scripts/hotkeys.pyc"
skipping non-regular file ".blender/scripts/image_auto_layout.py"
skipping non-regular file ".blender/scripts/image_auto_layout.pyc"
skipping non-regular file ".blender/scripts/image_billboard.py"
skipping non-regular file ".blender/scripts/image_billboard.pyc"
skipping non-regular file ".blender/scripts/image_edit.py"
skipping non-regular file ".blender/scripts/image_edit.pyc"
skipping non-regular file ".blender/scripts/image_find_paths.py"
skipping non-regular file ".blender/scripts/image_find_paths.pyc"
skipping non-regular file ".blender/scripts/import_dxf.py"
skipping non-regular file ".blender/scripts/import_dxf.pyc"
skipping non-regular file ".blender/scripts/import_mdd.py"
skipping non-regular file ".blender/scripts/import_mdd.pyc"
skipping non-regular file ".blender/scripts/import_obj.py"
skipping non-regular file ".blender/scripts/import_obj.pyc"
skipping non-regular file ".blender/scripts/kloputils.py"
skipping non-regular file ".blender/scripts/kloputils.pyc"
skipping non-regular file ".blender/scripts/kmz_ImportWithMesh.py"
skipping non-regular file ".blender/scripts/kmz_ImportWithMesh.pyc"
skipping non-regular file ".blender/scripts/knife.py"
skipping non-regular file ".blender/scripts/knife.pyc"
skipping non-regular file ".blender/scripts/lightwave_export.py"
skipping non-regular file ".blender/scripts/lightwave_export.pyc"
skipping non-regular file ".blender/scripts/lightwave_import.py"
skipping non-regular file ".blender/scripts/lightwave_import.pyc"
skipping non-regular file ".blender/scripts/md2_export.py"
skipping non-regular file ".blender/scripts/md2_export.pyc"
skipping non-regular file ".blender/scripts/md2_import.py"
skipping non-regular file ".blender/scripts/md2_import.pyc"
skipping non-regular file ".blender/scripts/mesh_bbrush_menu.py"
skipping non-regular file ".blender/scripts/mesh_bbrush_menu.pyc"
skipping non-regular file ".blender/scripts/mesh_boneweight_copy.py"
skipping non-regular file ".blender/scripts/mesh_boneweight_copy.pyc"
skipping non-regular file ".blender/scripts/mesh_cleanup.py"
skipping non-regular file ".blender/scripts/mesh_cleanup.pyc"
skipping non-regular file ".blender/scripts/mesh_edges2curves.py"
skipping non-regular file ".blender/scripts/mesh_edges2curves.pyc"
skipping non-regular file ".blender/scripts/mesh_mirror_tool.py"
skipping non-regular file ".blender/scripts/mesh_mirror_tool.pyc"
skipping non-regular file ".blender/scripts/mesh_poly_reduce.py"
skipping non-regular file ".blender/scripts/mesh_poly_reduce.pyc"
skipping non-regular file ".blender/scripts/mesh_skin.py"
skipping non-regular file ".blender/scripts/mesh_skin.pyc"
skipping non-regular file ".blender/scripts/mesh_solidify.py"
skipping non-regular file ".blender/scripts/mesh_solidify.pyc"
skipping non-regular file ".blender/scripts/mesh_tri2quad.py"
skipping non-regular file ".blender/scripts/mesh_tri2quad.pyc"
skipping non-regular file ".blender/scripts/mesh_unfolder.py"
skipping non-regular file ".blender/scripts/mesh_unfolder.pyc"
skipping non-regular file ".blender/scripts/mesh_wire.py"
skipping non-regular file ".blender/scripts/mesh_wire.pyc"
skipping non-regular file ".blender/scripts/mirror_bone_weights.py"
skipping non-regular file ".blender/scripts/mirror_bone_weights.pyc"
skipping non-regular file ".blender/scripts/nendo_export.py"
skipping non-regular file ".blender/scripts/nendo_export.pyc"
skipping non-regular file ".blender/scripts/nendo_import.py"
skipping non-regular file ".blender/scripts/nendo_import.pyc"
skipping non-regular file ".blender/scripts/obdatacopier.py"
skipping non-regular file ".blender/scripts/obdatacopier.pyc"
skipping non-regular file ".blender/scripts/obj_export.py"
skipping non-regular file ".blender/scripts/obj_export.pyc"
skipping non-regular file ".blender/scripts/obj_import.py"
skipping non-regular file ".blender/scripts/obj_import.pyc"
skipping non-regular file ".blender/scripts/object_apply_def.py"
skipping non-regular file ".blender/scripts/object_apply_def.pyc"
skipping non-regular file ".blender/scripts/object_batch_name_edit.py"
skipping non-regular file ".blender/scripts/object_batch_name_edit.pyc"
skipping non-regular file ".blender/scripts/object_cookie_cutter.py"
skipping non-regular file ".blender/scripts/object_cookie_cutter.pyc"
skipping non-regular file ".blender/scripts/object_drop.py"
skipping non-regular file ".blender/scripts/object_drop.pyc"
skipping non-regular file ".blender/scripts/object_find.py"
skipping non-regular file ".blender/scripts/object_find.pyc"
skipping non-regular file ".blender/scripts/object_random_loc_sz_rot.py"
skipping non-regular file ".blender/scripts/object_random_loc_sz_rot.pyc"
skipping non-regular file ".blender/scripts/object_sel2dupgroup.py"
skipping non-regular file ".blender/scripts/object_sel2dupgroup.pyc"
skipping non-regular file ".blender/scripts/off_export.py"
skipping non-regular file ".blender/scripts/off_export.pyc"
skipping non-regular file ".blender/scripts/off_import.py"
skipping non-regular file ".blender/scripts/off_import.pyc"
skipping non-regular file ".blender/scripts/paths_import.py"
skipping non-regular file ".blender/scripts/paths_import.pyc"
skipping non-regular file ".blender/scripts/ply_export.py"
skipping non-regular file ".blender/scripts/ply_export.pyc"
skipping non-regular file ".blender/scripts/ply_import.py"
skipping non-regular file ".blender/scripts/ply_import.pyc"
skipping non-regular file ".blender/scripts/radiosity_export.py"
skipping non-regular file ".blender/scripts/radiosity_export.pyc"
skipping non-regular file ".blender/scripts/radiosity_import.py"
skipping non-regular file ".blender/scripts/radiosity_import.pyc"
skipping non-regular file ".blender/scripts/raw_export.py"
skipping non-regular file ".blender/scripts/raw_export.pyc"
skipping non-regular file ".blender/scripts/raw_import.py"
skipping non-regular file ".blender/scripts/raw_import.pyc"
skipping non-regular file ".blender/scripts/renameobjectbyblock.py"
skipping non-regular file ".blender/scripts/renameobjectbyblock.pyc"
skipping non-regular file ".blender/scripts/rvk1_torvk2.py"
skipping non-regular file ".blender/scripts/rvk1_torvk2.pyc"
skipping non-regular file ".blender/scripts/save_theme.py"
skipping non-regular file ".blender/scripts/save_theme.pyc"
skipping non-regular file ".blender/scripts/scripttemplate_mesh_edit.py"
skipping non-regular file ".blender/scripts/scripttemplate_mesh_edit.pyc"
skipping non-regular file ".blender/scripts/scripttemplate_object_edit.py"
skipping non-regular file ".blender/scripts/scripttemplate_object_edit.pyc"
skipping non-regular file ".blender/scripts/slp_import.py"
skipping non-regular file ".blender/scripts/slp_import.pyc"
skipping non-regular file ".blender/scripts/sysinfo.py"
skipping non-regular file ".blender/scripts/sysinfo.pyc"
skipping non-regular file ".blender/scripts/tex2uvbaker.py"
skipping non-regular file ".blender/scripts/tex2uvbaker.pyc"
skipping non-regular file ".blender/scripts/truespace_export.py"
skipping non-regular file ".blender/scripts/truespace_export.pyc"
skipping non-regular file ".blender/scripts/truespace_import.py"
skipping non-regular file ".blender/scripts/truespace_import.pyc"
skipping non-regular file ".blender/scripts/unweld.py"
skipping non-regular file ".blender/scripts/unweld.pyc"
skipping non-regular file ".blender/scripts/uv_archimap.py"
skipping non-regular file ".blender/scripts/uv_archimap.pyc"
skipping non-regular file ".blender/scripts/uv_auto_layout_tex.py"
skipping non-regular file ".blender/scripts/uv_auto_layout_tex.pyc"
skipping non-regular file ".blender/scripts/uv_export.py"
skipping non-regular file ".blender/scripts/uv_export.pyc"
skipping non-regular file ".blender/scripts/uv_from_adjacent.py"
skipping non-regular file ".blender/scripts/uv_from_adjacent.pyc"
skipping non-regular file ".blender/scripts/uv_relax.py"
skipping non-regular file ".blender/scripts/uv_relax.pyc"
skipping non-regular file ".blender/scripts/uv_seams_from_islands.py"
skipping non-regular file ".blender/scripts/uv_seams_from_islands.pyc"
skipping non-regular file ".blender/scripts/uvcalc_follow_active_coords.py"
skipping non-regular file ".blender/scripts/uvcalc_follow_active_coords.pyc"
skipping non-regular file ".blender/scripts/uvcalc_from_adjacent.py"
skipping non-regular file ".blender/scripts/uvcalc_from_adjacent.pyc"
skipping non-regular file ".blender/scripts/uvcalc_lightmap.py"
skipping non-regular file ".blender/scripts/uvcalc_lightmap.pyc"
skipping non-regular file ".blender/scripts/uvcalc_quad_clickproj.py"
skipping non-regular file ".blender/scripts/uvcalc_quad_clickproj.pyc"
skipping non-regular file ".blender/scripts/uvcalc_smart_project.py"
skipping non-regular file ".blender/scripts/uvcalc_smart_project.pyc"
skipping non-regular file ".blender/scripts/uvcopy.py"
skipping non-regular file ".blender/scripts/uvcopy.pyc"
skipping non-regular file ".blender/scripts/uvpaint.py"
skipping non-regular file ".blender/scripts/uvpaint.pyc"
skipping non-regular file ".blender/scripts/vertexpaint_from_material.py"
skipping non-regular file ".blender/scripts/vertexpaint_from_material.pyc"
skipping non-regular file ".blender/scripts/vertexpaint_gradient.py"
skipping non-regular file ".blender/scripts/vertexpaint_gradient.pyc"
skipping non-regular file ".blender/scripts/vertexpaint_selfshadow_ao.py"
skipping non-regular file ".blender/scripts/vertexpaint_selfshadow_ao.pyc"
skipping non-regular file ".blender/scripts/videoscape_export.py"
skipping non-regular file ".blender/scripts/videoscape_export.pyc"
skipping non-regular file ".blender/scripts/vrml97_export.py"
skipping non-regular file ".blender/scripts/vrml97_export.pyc"
skipping non-regular file ".blender/scripts/weightpaint_clean.py"
skipping non-regular file ".blender/scripts/weightpaint_clean.pyc"
skipping non-regular file ".blender/scripts/weightpaint_copy.py"
skipping non-regular file ".blender/scripts/weightpaint_copy.pyc"
skipping non-regular file ".blender/scripts/weightpaint_envelope_assign.py"
skipping non-regular file ".blender/scripts/weightpaint_envelope_assign.pyc"
skipping non-regular file ".blender/scripts/weightpaint_gradient.py"
skipping non-regular file ".blender/scripts/weightpaint_gradient.pyc"
skipping non-regular file ".blender/scripts/weightpaint_grow_shrink.py"
skipping non-regular file ".blender/scripts/weightpaint_grow_shrink.pyc"
skipping non-regular file ".blender/scripts/weightpaint_normalize.py"
skipping non-regular file ".blender/scripts/weightpaint_normalize.pyc"
skipping non-regular file ".blender/scripts/widgetwizard.py"
skipping non-regular file ".blender/scripts/widgetwizard.pyc"
skipping non-regular file ".blender/scripts/x3d_export.py"
skipping non-regular file ".blender/scripts/x3d_export.pyc"
skipping non-regular file ".blender/scripts/xfig_export.py"
skipping non-regular file ".blender/scripts/xfig_export.pyc"
skipping non-regular file ".blender/scripts/xsi_export.py"
skipping non-regular file ".blender/scripts/xsi_export.pyc"
.bogofilter/wordlist.db
.cache/tracker/email-index.db
.cache/tracker/file-index.db
.cache/tracker/file-update-index.db
.config/gtk-2.0/gtkfilechooser.ini
.evolution/.running
.evolution/camel-cert.db
.evolution/cache/tmp/mail.log.GJGc2S
.evolution/cache/tmp/mail.log.YYKrY4
.evolution/calendar/searches.xml
.evolution/calendar/config/TaskPad
.evolution/calendar/local/1196113206.6282.2@garrett-desktop/calendar.ics
.evolution/calendar/local/1196125753.6282.43@garrett-desktop/calendar.ics
.evolution/calendar/local/system/calendar.ics
.evolution/mail/searches.xml
.evolution/mail/config/et-expanded-imap:__garrett@mail.garrettsites.net_INBOX
.evolution/mail/config/et-expanded-imap:__garrett@mail.garrettsites.net_INBOX_Business_Decade_20of_20ED
.evolution/mail/config/et-expanded-mbox:_home_garrett_.evolution_mail_local_Drafts
.evolution/mail/config/et-expanded-mbox:_home_garrett_.evolution_mail_local_Inbox
.evolution/mail/config/folder-tree-expand-state.xml
.evolution/mail/config/gtkrc-mail-fonts
.evolution/mail/imap/garrett@mail.garrettsites.net/.ev-store-summary
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14869.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14870.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14871.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14873.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14874.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14876.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/14877.
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/summary
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/summary-meta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/Amenity Website/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/Computer Medics/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/Decade of ED/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/Drager Wedding/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/Life Website/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/New Ground Water Project/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Business/subfolders/eBay Transactions/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Drafts/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/INBOX/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/INBOX/subfolders/Drafts/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/INBOX/subfolders/Sent/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/INBOX/subfolders/Trash/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Random saved email/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Sent/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Texas De Brazil/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/Trash/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/courierimapsubscribed/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/courierimapuiddb/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/saved-messages/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/sent-mail/cmeta
.evolution/mail/imap/garrett@mail.garrettsites.net/folders/INBOX/subfolders/smsrecieve@garrettsites_net/cmeta
.evolution/mail/local/Drafts.cmeta
.evolution/mail/local/Inbox.cmeta
.evolution/mail/local/Outbox
.evolution/mail/local/Outbox.cmeta
.evolution/mail/local/Outbox.ev-summary
.evolution/mail/local/Outbox.ev-summary-meta
.evolution/mail/local/Outbox.ibex.index
.evolution/mail/local/Outbox.ibex.index.data
.evolution/mail/local/Sent
.evolution/mail/local/Sent.cmeta
.evolution/mail/local/Sent.ev-summary
.evolution/mail/local/Sent.ev-summary-meta
.evolution/mail/local/Sent.ibex.index
.evolution/mail/local/Sent.ibex.index.data
.evolution/memos/config/MemoPad
.evolution/memos/local/system/journal.ics
.evolution/tasks/local/1196027872.8130.0@garrett-desktop/tasks.ics
.evolution/tasks/local/1196291058.6216.2@garrett-desktop/tasks.ics
.evolution/tasks/local/system/tasks.ics
skipping non-regular file ".gaim/guifications"
skipping non-regular file ".gaim/logs"
skipping non-regular file ".gaim/smileys"
.gconf/GNOME/Spell/%gconf.xml
.gconf/apps/aisleriot/%gconf.xml
.gconf/apps/compiz/general/allscreens/options/%gconf.xml
.gconf/apps/compiz/plugins/expo/allscreens/options/%gconf.xml
.gconf/apps/compiz/plugins/scale/allscreens/options/%gconf.xml
.gconf/apps/deskbar/%gconf.xml
.gconf/apps/eog/ui/%gconf.xml
.gconf/apps/evolution/%gconf.xml
.gconf/apps/evolution/calendar/display/%gconf.xml
.gconf/apps/evolution/mail/%gconf.xml
.gconf/apps/evolution/mail/composer/%gconf.xml
.gconf/apps/evolution/mail/display/%gconf.xml
.gconf/apps/evolution/mail/message_window/%gconf.xml
.gconf/apps/evolution/shell/%gconf.xml
.gconf/apps/evolution/shell/view_defaults/%gconf.xml
.gconf/apps/evolution/shell/view_defaults/folder_bar/%gconf.xml
.gconf/apps/file-roller/listing/%gconf.xml
.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml
.gconf/apps/gnome-screensaver/%gconf.xml
.gconf/apps/metacity/general/%gconf.xml
.gconf/apps/nautilus-cd-burner/%gconf.xml
.gconf/apps/nautilus-cd-burner/garrett-desktop/%gconf.xml
.gconf/apps/nautilus/preferences/%gconf.xml
.gconf/apps/panel/applets/applet_0/prefs/%gconf.xml
.gconf/apps/panel/applets/clock_screen0/prefs/%gconf.xml
.gconf/apps/panel/applets/window_list_screen0/prefs/%gconf.xml
.gconf/apps/panel/applets/workspace_switcher_screen0/prefs/%gconf.xml
.gconf/apps/procman/%gconf.xml
.gconf/apps/procman/disktreenew/%gconf.xml
.gconf/apps/procman/proctree/%gconf.xml
.gconf/desktop/gnome/applications/window_manager/%gconf.xml
.gconf/desktop/gnome/background/%gconf.xml
.gconf/desktop/gnome/font_rendering/%gconf.xml
.gconf/desktop/gnome/interface/%gconf.xml
.gconf/desktop/gnome/peripherals/keyboard/host-garrett-desktop/0/%gconf.xml
.gconf/desktop/gnome/peripherals/mouse/%gconf.xml
.gconfd/saved_state
.gnome2/accelsgedit
.gnome2/backgrounds.xml
.gnome2/gedit-2
.gnome2/gedit-metadata.xml
.gnome2/main
.gnome2/yelp
.gnome2/accels/aisleriot
.gnome2/accels/eog
.gnome2/nautilus-sendto/pidgin_buddies_online
.gnome2/share/cursor-fonts/fonts.dir
.gnome2/share/fonts/fonts.dir
skipping non-regular file ".gnome2_ubuntu/seahorse-1KCzSX/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-4ke857/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-4us3dx/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-5VB46w/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-8D7JqY/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-8QHm18/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-947mGM/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-96BgVj/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-9eGSrd/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-AJ4hBl/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-Bf9G9A/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-BfsyPl/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-D67x9r/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-DHjBbs/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-ENpIeZ/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-EeULTR/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-HALvcc/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-HoHNzy/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-IGcPnJ/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-If67kd/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-IvJJ52/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-JAyA8C/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-JZ2XKP/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-K1Unjy/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-Lb6j5H/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-NOTDUY/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-O5HVxG/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-OwkWNY/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-P6NGaK/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-R6CWPK/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-SWX7Lk/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-SyTK2e/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-T2AdxD/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-TLOeiW/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-UhNXR7/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-UrX5Ns/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-VDDq7j/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-WCWjuC/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-WHUJuU/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-Wv8brv/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-Y8ZiG0/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-YORDBf/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-YZvII5/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-YitMCs/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-YqfZnb/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-ZbycbP/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-Zccc1F/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-aLGXzG/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-aOGorL/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-apL3xH/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-cEtkye/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-cRhjoi/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-cYRMKf/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-dS7NMq/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-dkOkWR/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-gVL7xl/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-gowTSs/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-h79mGr/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-hAM7Jx/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-hrRjRR/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-j1Km4t/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-k3b7Wf/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-mNGBcA/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-nUrc3R/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-o8DuXP/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-pJTV4S/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-pSAhfU/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-qQcTkN/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-tmlBJD/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-uhkuzh/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-vKbRP6/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-vZbfDX/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-vjl4Ca/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-wPjBni/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-wSpcTR/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-zXYyFP/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-zm2cQn/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/seahorse-zskKNQ/S.gpg-agent"
skipping non-regular file ".gnome2_ubuntu/totem-addons/AvidQTAVUICodec.qtx"
skipping non-regular file ".gnome2_ubuntu/totem-addons/BeHereiVideo.qtx"
skipping non-regular file ".gnome2_ubuntu/totem-addons/CLRVIDDC.DLL"
skipping non-regular file ".gnome2_ubuntu/totem-addons/CtWbJpg.DLL"
skipping non-regular file ".gnome2_ubuntu/totem-addons/DECVW_32.DLL"
skipping non-regular file ".gnome2_ubuntu/totem-addons/LCMW2.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/LCODCCMW2E.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/LCodcCMP.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/QuickTime.qts"
skipping non-regular file ".gnome2_ubuntu/totem-addons/QuickTimeEssentials.qtx"
skipping non-regular file ".gnome2_ubuntu/totem-addons/QuickTimeInternetExtras.qtx"
skipping non-regular file ".gnome2_ubuntu/totem-addons/VDODEC32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ViVD2.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/acelpdec.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/alf2cd.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/aslcodec_dshow.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/aslcodec_vfw.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/asusasv2.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/asusasvd.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ativcr2.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/atrac3.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/atrc.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/avimszh.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/avizlib.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/clrviddd.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/cook.so"
skipping non-regular file ".gnome2_ubuntu/totem-addons/cook.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ctadp32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ddnt.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/divx.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/divx_c32.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/divxa32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/divxc32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/divxdec.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/dnet.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/drv2.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/drv3.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/drv4.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/drvc.so"
skipping non-regular file ".gnome2_ubuntu/totem-addons/dspr.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/huffyuv.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/i263_32.drv"
skipping non-regular file ".gnome2_ubuntu/totem-addons/iac25_32.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/iccvid.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/icmw_32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/imaadp32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/imc32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ir32_32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ir41_32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ir50_32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ivvideo.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/jp2avi.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/l3codeca.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/l3codecx.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/lhacm.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/lsvxdec.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/m3jp2k32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/m3jpeg32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/m3jpegdec.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/mcdvd_32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/mcmjpg32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/mi-sc4.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/mpg4c32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/mpg4ds32.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msadp32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msg711.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msgsm32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msh261.drv"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msms001.vwp"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msnaudio.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msrle32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msscds32.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/msvidc32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/mvoiced.vwp"
skipping non-regular file ".gnome2_ubuntu/totem-addons/nsrt2432.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/pclepim1.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/qdv.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/qpeg32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/qtmlClient.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/rt32dcmp.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/scg726.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/sipr.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/sp5x_32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tm20dec.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tokf.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tokr.so.6.0"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tsccvid.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tsd32.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tssoft32.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/tvqdec.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ubv263d+.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ubvmp4d.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/ultimo.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vdowave.drv"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vgpix32d.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_3ivX.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_cvid.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_cyuv.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_h261.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_h263.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_iv32.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_iv41.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vid_iv50.xa"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vivog723.acm"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vmnc.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/voxmsdec.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vp31vfw.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vp4vfw.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vp5vfw.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vp6vfw.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vp7vfw.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vssh264.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vssh264core.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vssh264dec.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vsshdsd.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vsslight.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/vsswlt.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wma9dmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmadmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmsdmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmspdmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmv8ds32.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmv9dmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmvadvd.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmvdmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wmvds32.ax"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wnvplay1.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wnvwinx.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/wvc1dmod.dll"
skipping non-regular file ".gnome2_ubuntu/totem-addons/zmbv.dll"
skipping non-regular file ".googleearth/instance-running-lock"
skipping non-regular file ".gxine/socket"
skipping non-regular file ".kde/cache-garrett-desktop"
skipping non-regular file ".kde/cache-garrett-ubuntu"
skipping non-regular file ".kde/socket-garrett-desktop"
skipping non-regular file ".kde/socket-garrett-ubuntu"
skipping non-regular file ".kde/tmp-garrett-desktop"
skipping non-regular file ".kde/tmp-garrett-ubuntu"
.kde/share/apps/amarok/contextbrowser.html
.kde/share/apps/amarok/current.xml
.kde/share/apps/amarok/dynamicbrowser_save.xml
.kde/share/apps/amarok/lastfmbrowser_save.xml
.kde/share/apps/amarok/playlistbrowser_save.xml
.kde/share/apps/amarok/smartplaylistbrowser_save.xml
.kde/share/apps/amarok/statusbar.log.3
.kde/share/apps/amarok/streambrowser_save.xml
.kde/share/apps/amarok/submit.xml
.kde/share/apps/amarok/transferlist.xml
.kde/share/apps/amarok/xine-config
.kde/share/apps/amarok/albumcovers/cache/130@0196301d686558a5094352ff82267b5e@shadow
.kde/share/apps/amarok/albumcovers/cache/130@09f0fb3f7b15521512e9f2e339ca4f0a@shadow
.kde/share/apps/amarok/albumcovers/cache/130@160abae485e097f3859289b48652fb90@shadow
.kde/share/apps/amarok/albumcovers/cache/130@307778e35123c23233ac6859f89a2a2c@shadow
.kde/share/apps/amarok/albumcovers/cache/130@31f3c861e03bae0e2857840b8c3f1383@shadow
.kde/share/apps/amarok/albumcovers/cache/130@351b2d2fbd67af20798666e7ddeb3c18@shadow
.kde/share/apps/amarok/albumcovers/cache/130@3698990e0889e216658198118a04c77d@shadow
.kde/share/apps/amarok/albumcovers/cache/130@5433a4c145a4aba7d273bf62ebbd4c6d@shadow
.kde/share/apps/amarok/albumcovers/cache/130@5a3fa290aa9ea130c45c830adfa59cf8@shadow
.kde/share/apps/amarok/albumcovers/cache/130@5e2a67a2a72001995cc20f9897e06463@shadow
.kde/share/apps/amarok/albumcovers/cache/130@67632d891e7610d06ab78eca1b8a801d@shadow
.kde/share/apps/amarok/albumcovers/cache/130@6ac89819fe85062487a985455979e3d7@shadow
.kde/share/apps/amarok/albumcovers/cache/130@a267ec991f16496e379875164238b135@shadow
.kde/share/apps/amarok/albumcovers/cache/130@a2fb3e94871dd31685a4a4f3f156805b@shadow
.kde/share/apps/amarok/albumcovers/cache/130@a69a85a67652417bb73e9b2431ddcd7e@shadow
.kde/share/apps/amarok/albumcovers/cache/130@aab86fa1e462340afa77356d19cde71f@shadow
.kde/share/apps/amarok/albumcovers/cache/130@b63934986c4f5fd4f9547b580bb024a4@shadow
.kde/share/apps/amarok/albumcovers/cache/130@b8b5847a33b249f0d8733f7e66027feb@shadow
.kde/share/apps/amarok/albumcovers/cache/130@ba07759026a30643d0a301820ef20491@shadow
.kde/share/apps/amarok/albumcovers/cache/130@ba44d08c9cfe41520361c63ed7309c29@shadow
.kde/share/apps/amarok/albumcovers/cache/130@bc6f39e311b1d44f48a628e9c0ded601@shadow
.kde/share/apps/amarok/albumcovers/cache/130@c40d2658228d56905e21f72a2b5cb39a@shadow
.kde/share/apps/amarok/albumcovers/cache/130@d78768ee02c0e3db69b2afef5a8106bd@shadow
.kde/share/apps/amarok/albumcovers/cache/130@e8f63730c0d40afb1520ac401cb6b2ee@shadow
.kde/share/apps/amarok/albumcovers/cache/130@f2f7c03f4b7303183f9b60da21298c65@shadow
.kde/share/apps/amarok/albumcovers/cache/130@nocover.png
.kde/share/apps/amarok/albumcovers/cache/150@09f0fb3f7b15521512e9f2e339ca4f0a
.kde/share/apps/amarok/albumcovers/cache/150@09f0fb3f7b15521512e9f2e339ca4f0a@shadow
.kde/share/apps/amarok/albumcovers/cache/150@3698990e0889e216658198118a04c77d
.kde/share/apps/amarok/albumcovers/cache/150@3698990e0889e216658198118a04c77d@shadow
.kde/share/apps/amarok/albumcovers/cache/150@67632d891e7610d06ab78eca1b8a801d
.kde/share/apps/amarok/albumcovers/cache/150@67632d891e7610d06ab78eca1b8a801d@shadow
.kde/share/apps/amarok/albumcovers/cache/50@04ac268dfacd81dff18a28de27ee43da@shadow
.kde/share/apps/amarok/albumcovers/cache/50@0809382232f999bdc34a2f7f6e3b7d67@shadow
.kde/share/apps/amarok/albumcovers/cache/50@095e358e0a820cf56331c12e78735aa2@shadow
.kde/share/apps/amarok/albumcovers/cache/50@09f0fb3f7b15521512e9f2e339ca4f0a@shadow
.kde/share/apps/amarok/albumcovers/cache/50@160abae485e097f3859289b48652fb90@shadow
.kde/share/apps/amarok/albumcovers/cache/50@186984f02b26a40fa2320d0646722dd3@shadow
.kde/share/apps/amarok/albumcovers/cache/50@2db4ccfc688068516b2bd2cd6a3a49e8@shadow
.kde/share/apps/amarok/albumcovers/cache/50@3042ecb976c473885621e164dc0fd824@shadow
.kde/share/apps/amarok/albumcovers/cache/50@3241ec4efa56d4d1843788f6f8dfccb7@shadow
.kde/share/apps/amarok/albumcovers/cache/50@351b2d2fbd67af20798666e7ddeb3c18@shadow
.kde/share/apps/amarok/albumcovers/cache/50@38a0ab06b47d392c687f98a0add5117e@shadow
.kde/share/apps/amarok/albumcovers/cache/50@3a167b2981ae4e1e7de2bb909c0be813@shadow
.kde/share/apps/amarok/albumcovers/cache/50@41b278322b69b31e2153c1723d170c44@shadow
.kde/share/apps/amarok/albumcovers/cache/50@554f94e4f367547cd00b003659ad3242@shadow
.kde/share/apps/amarok/albumcovers/cache/50@55ad42322b4f15661dae3552340607d6@shadow
.kde/share/apps/amarok/albumcovers/cache/50@5c69b4102754f1f37016efcd8f527d04@shadow
.kde/share/apps/amarok/albumcovers/cache/50@5ede6a38ebb01b4c065b7300677d7f68@shadow
.kde/share/apps/amarok/albumcovers/cache/50@601ca218e0f63abb0ff6500499ba2cfd@shadow
.kde/share/apps/amarok/albumcovers/cache/50@61e740df0a3e37384dc02da1b39de3f4@shadow
.kde/share/apps/amarok/albumcovers/cache/50@6666be7d1a2831a9986e314b4dde3540@shadow
.kde/share/apps/amarok/albumcovers/cache/50@67632d891e7610d06ab78eca1b8a801d@shadow
.kde/share/apps/amarok/albumcovers/cache/50@688399134146cf6d28bf0cfb6248b633@shadow
.kde/share/apps/amarok/albumcovers/cache/50@68b7d27e6dbdd7d24714745b08bdca88@shadow
.kde/share/apps/amarok/albumcovers/cache/50@695dedabb4dfb79c5037dea488c9e262@shadow
.kde/share/apps/amarok/albumcovers/cache/50@6ac89819fe85062487a985455979e3d7@shadow
.kde/share/apps/amarok/albumcovers/cache/50@6de8a5787f7f8b8536d7ab647ec3ddc6@shadow
.kde/share/apps/amarok/albumcovers/cache/50@845ae5ef170e0e123097a3aa4c591b21@shadow
.kde/share/apps/amarok/albumcovers/cache/50@87676150b22f575f3a365cb7f1082e30@shadow
.kde/share/apps/amarok/albumcovers/cache/50@87cf21428e4545a01a3a5b31294bdc7b@shadow
.kde/share/apps/amarok/albumcovers/cache/50@903a0f2816809886f47139acabbe7c1b@shadow
.kde/share/apps/amarok/albumcovers/cache/50@976f4316178406d03104e1667644d344@shadow
.kde/share/apps/amarok/albumcovers/cache/50@9eb853c10931c3ec30fba39367ceb8af@shadow
.kde/share/apps/amarok/albumcovers/cache/50@a267ec991f16496e379875164238b135@shadow
.kde/share/apps/amarok/albumcovers/cache/50@a2c5ebfe86471c4762530157ce96beac@shadow
.kde/share/apps/amarok/albumcovers/cache/50@a69a85a67652417bb73e9b2431ddcd7e@shadow
.kde/share/apps/amarok/albumcovers/cache/50@aab86fa1e462340afa77356d19cde71f@shadow
.kde/share/apps/amarok/albumcovers/cache/50@ada3427538617fe242c8ca6123b0379e@shadow
.kde/share/apps/amarok/albumcovers/cache/50@b63934986c4f5fd4f9547b580bb024a4@shadow
.kde/share/apps/amarok/albumcovers/cache/50@b8b5847a33b249f0d8733f7e66027feb@shadow
.kde/share/apps/amarok/albumcovers/cache/50@ba07759026a30643d0a301820ef20491@shadow
.kde/share/apps/amarok/albumcovers/cache/50@ba44d08c9cfe41520361c63ed7309c29@shadow
.kde/share/apps/amarok/albumcovers/cache/50@bcdb015c19b57a1e5bb40920e782b07e@shadow
.kde/share/apps/amarok/albumcovers/cache/50@bd50f2348c9050e760cea1e0575ce002@shadow
.kde/share/apps/amarok/albumcovers/cache/50@bd904fd1f29a91ff93dc3c83a5b28229@shadow
.kde/share/apps/amarok/albumcovers/cache/50@bef2b2f2021d879b50ba1ce7a05dfb53@shadow
.kde/share/apps/amarok/albumcovers/cache/50@c1557e83a80b6683f3f0621c9a479eba@shadow
.kde/share/apps/amarok/albumcovers/cache/50@c40d2658228d56905e21f72a2b5cb39a@shadow
.kde/share/apps/amarok/albumcovers/cache/50@c8d40f001b32430040516337effe1433@shadow
.kde/share/apps/amarok/albumcovers/cache/50@d068a5ca31edbbfd27c056e96e91c9d0@shadow
.kde/share/apps/amarok/albumcovers/cache/50@d52530792b3a067493817fe5822ad04e@shadow
.kde/share/apps/amarok/albumcovers/cache/50@d78768ee02c0e3db69b2afef5a8106bd@shadow
.kde/share/apps/amarok/albumcovers/cache/50@e8f63730c0d40afb1520ac401cb6b2ee@shadow
.kde/share/apps/amarok/albumcovers/cache/50@e9b29e8029201c94fdb60cc5a04905ab@shadow
.kde/share/apps/amarok/albumcovers/cache/50@ee3a9d9b8c61fefc0cffc0b3efc95aa7@shadow
.kde/share/apps/amarok/albumcovers/cache/50@f2f7c03f4b7303183f9b60da21298c65@shadow
.kde/share/apps/amarok/albumcovers/cache/50@f55eda5795a810b20409150850794cc6@shadow
.kde/share/apps/amarok/albumcovers/cache/50@fc808d6aae9e1ad56da6e8243aac4f08@shadow
.kde/share/apps/amarok/albumcovers/cache/50@fe75aa8787d8cd90040c0b604d7e3dae@shadow
.kde/share/apps/amarok/albumcovers/cache/50@fe95fb7f4e1da72095b009cbcd085de3@shadow
.kde/share/apps/amarok/albumcovers/cache/50@nocover.png
.kde/share/apps/amarok/albumcovers/tagcover/4d66969abf2197d7a086f349290f32bf
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover100x99.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover112x100.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover137x121.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover137x135.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover159x141.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover159x156.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover159x157.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover53x47.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover53x53.png
.kde/share/apps/amarok/covershadow-cache/shadow_albumcover54x54.png
.kde/share/apps/amarok/undo/1.xml
.kde/share/apps/amarok/undo/11.xml
.kde/share/apps/amarok/undo/12.xml
.kde/share/apps/amarok/undo/13.xml
.kde/share/apps/amarok/undo/14.xml
.kde/share/apps/amarok/undo/15.xml
.kde/share/apps/amarok/undo/16.xml
.kde/share/apps/amarok/undo/17.xml
.kde/share/apps/amarok/undo/18.xml
.kde/share/apps/amarok/undo/19.xml
.kde/share/apps/amarok/undo/20.xml
.kde/share/apps/amarok/undo/21.xml
.kde/share/apps/amarok/undo/22.xml
.kde/share/apps/amarok/undo/23.xml
.kde/share/apps/amarok/undo/24.xml
.kde/share/apps/amarok/undo/25.xml
.kde/share/apps/amarok/undo/26.xml
.kde/share/apps/amarok/undo/27.xml
.kde/share/apps/kcookiejar/cookies
.kde/share/config/amarokrc
.kde/share/config/kdeglobals
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/PlaNed.nfo
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Ad-AwareSE/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Ad-AwareSE/Ad-AwareSE_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/AntiVirPersonal/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/AntiVirPersonal/AntiVirPersonal_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Avast!BartCD/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Avast!BartCD/DATA/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Avast!BartCD/DATA/400.vps
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/CATALOG.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/ECMSVR32.DLL
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/NAVENG32.DLL
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/NAVEX32A.DLL
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/SCRAUTH.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TCDEFS.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TCSCAN7.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TCSCAN8.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TCSCAN9.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TINF.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TINFIDX.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TINFL.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TSCAN1.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/TSCAN1HD.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN1.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN2.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN3.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN4.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN5.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN6.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN7.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN8.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/VIRSCAN9.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NAV/VirusDef/ZDONE.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NOD32AntiVirus/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/NOD32AntiVirus/NOD32AntiVirus_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/SpybotSD/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/SpybotSD/SpybotSD_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/TrendMicroSysClean/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/TrendMicroSysClean/SysClean_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Utilities/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/Utilities/a2AntiTrojan_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/License.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/Messages.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/SCANGUI.EXE
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/Scan.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/avparam.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/clean.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/internet.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/mcscan32.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/names.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/packing.lst
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/psapi.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/rwabs16.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/rwabs32.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25 (2)/Programs/mcafee/scan.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/PlaNed.nfo
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Ad-AwareSE/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Ad-AwareSE/Ad-AwareSE_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/AntiVirPersonal/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/AntiVirPersonal/AntiVirPersonal_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Avast!BartCD/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Avast!BartCD/DATA/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Avast!BartCD/DATA/400.vps
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/CATALOG.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/ECMSVR32.DLL
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/NAVENG32.DLL
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/NAVEX32A.DLL
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/SCRAUTH.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TCDEFS.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TCSCAN7.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TCSCAN8.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TCSCAN9.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TINF.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TINFIDX.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TINFL.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TSCAN1.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/TSCAN1HD.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN1.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN2.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN3.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN4.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN5.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN6.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN7.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN8.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/VIRSCAN9.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NAV/VirusDef/ZDONE.DAT
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NOD32AntiVirus/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/NOD32AntiVirus/NOD32AntiVirus_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/SpybotSD/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/SpybotSD/SpybotSD_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/TrendMicroSysClean/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/TrendMicroSysClean/SysClean_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Utilities/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/Utilities/a2AntiTrojan_SFX.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/License.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/Messages.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/SCANGUI.EXE
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/Scan.exe
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/avparam.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/clean.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/internet.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/mcscan32.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/names.dat
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/packing.lst
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/psapi.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/rwabs16.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/rwabs32.dll
.local/share/Trash/files/miniPE.AV.Update.2oo8.o4.25/Programs/mcafee/scan.dat
.local/share/Trash/info/miniPE.AV.Update.2oo8.o4.25 (2).trashinfo
.local/share/Trash/info/miniPE.AV.Update.2oo8.o4.25.trashinfo
.local/share/tracker/data/common.db
skipping non-regular file ".loki/installed/google-earth.xml"
.macromedia/Flash_Player/#SharedObjects/URFDA8KA/youtube.com/soundData.sol
.macromedia/Flash_Player/#SharedObjects/URFDA8KA/youtube.com/videostats.sol
.mozilla/firefox/jur1232x.default/.parentlock
.mozilla/firefox/jur1232x.default/XPC.mfasl
.mozilla/firefox/jur1232x.default/XUL.mfasl
.mozilla/firefox/jur1232x.default/blocklist.xml
.mozilla/firefox/jur1232x.default/cert8.db
.mozilla/firefox/jur1232x.default/cookies.sqlite
.mozilla/firefox/jur1232x.default/downloads.sqlite
.mozilla/firefox/jur1232x.default/key3.db
.mozilla/firefox/jur1232x.default/localstore.rdf
skipping non-regular file ".mozilla/firefox/jur1232x.default/lock"
.mozilla/firefox/jur1232x.default/places.sqlite
.mozilla/firefox/jur1232x.default/places.sqlite-journal
.mozilla/firefox/jur1232x.default/pluginreg.dat
.mozilla/firefox/jur1232x.default/prefs.js
.mozilla/firefox/jur1232x.default/secmod.db
.mozilla/firefox/jur1232x.default/sessionstore.js
.mozilla/firefox/jur1232x.default/signons3.txt
.mozilla/firefox/jur1232x.default/urlclassifier3.sqlite
.mozilla/firefox/jur1232x.default/urlclassifier3.sqlite-journal
.mozilla/firefox/jur1232x.default/urlclassifierkey3.txt
.mozilla/firefox/jur1232x.default/Cache/00EE8C7Cd01
.mozilla/firefox/jur1232x.default/Cache/05CCD007d01
.mozilla/firefox/jur1232x.default/Cache/05EEDC29d01
.mozilla/firefox/jur1232x.default/Cache/06CCE034d01
.mozilla/firefox/jur1232x.default/Cache/06EEEC1Ad01
.mozilla/firefox/jur1232x.default/Cache/096FB213d01
.mozilla/firefox/jur1232x.default/Cache/0BE68530d01
.mozilla/firefox/jur1232x.default/Cache/0D6BCFBFd01
.mozilla/firefox/jur1232x.default/Cache/0F2915BDd01
.mozilla/firefox/jur1232x.default/Cache/0FEE7C83d01
.mozilla/firefox/jur1232x.default/Cache/11CD9153d01
.mozilla/firefox/jur1232x.default/Cache/11EF9D7Dd01
.mozilla/firefox/jur1232x.default/Cache/12CDA160d01
.mozilla/firefox/jur1232x.default/Cache/12EFA340d01
.mozilla/firefox/jur1232x.default/Cache/12EFAD4Ed01
.mozilla/firefox/jur1232x.default/Cache/17CDF135d01
.mozilla/firefox/jur1232x.default/Cache/17EFFD1Bd01
.mozilla/firefox/jur1232x.default/Cache/1812EE0Ed01
.mozilla/firefox/jur1232x.default/Cache/1DC3146Cd01
.mozilla/firefox/jur1232x.default/Cache/23CEB241d01
.mozilla/firefox/jur1232x.default/Cache/24CEC236d01
.mozilla/firefox/jur1232x.default/Cache/2508F568d01
.mozilla/firefox/jur1232x.default/Cache/25283627d01
.mozilla/firefox/jur1232x.default/Cache/27ECFE2Bd01
.mozilla/firefox/jur1232x.default/Cache/285ABC9Ad01
.mozilla/firefox/jur1232x.default/Cache/2C5A7307d01
.mozilla/firefox/jur1232x.default/Cache/2D66A356d01
.mozilla/firefox/jur1232x.default/Cache/2D7810C6d01
.mozilla/firefox/jur1232x.default/Cache/2ECE629Cd01
.mozilla/firefox/jur1232x.default/Cache/30CF8362d01
.mozilla/firefox/jur1232x.default/Cache/33EDBF7Fd01
.mozilla/firefox/jur1232x.default/Cache/33EED0A9d01
.mozilla/firefox/jur1232x.default/Cache/34EDCF08d01
.mozilla/firefox/jur1232x.default/Cache/35CFD337d01
.mozilla/firefox/jur1232x.default/Cache/36AA8D26d01
.mozilla/firefox/jur1232x.default/Cache/36CFE304d01
.mozilla/firefox/jur1232x.default/Cache/37E6A353d01
.mozilla/firefox/jur1232x.default/Cache/37E7C543d01
.mozilla/firefox/jur1232x.default/Cache/37E7C5DBd01
.mozilla/firefox/jur1232x.default/Cache/3E6BB3BAd01
.mozilla/firefox/jur1232x.default/Cache/3EED6FA2d01
.mozilla/firefox/jur1232x.default/Cache/3FCF739Dd01
.mozilla/firefox/jur1232x.default/Cache/400DF304d01
.mozilla/firefox/jur1232x.default/Cache/4147C6C5d01
.mozilla/firefox/jur1232x.default/Cache/4147C6CFd01
.mozilla/firefox/jur1232x.default/Cache/43AE8675d01
.mozilla/firefox/jur1232x.default/Cache/448CD600d01
.mozilla/firefox/jur1232x.default/Cache/44AED622d01
.mozilla/firefox/jur1232x.default/Cache/4E99C11Ad01
.mozilla/firefox/jur1232x.default/Cache/4EAE7688d01
.mozilla/firefox/jur1232x.default/Cache/4F04020Ed01
.mozilla/firefox/jur1232x.default/Cache/4FA1A7D8d01
.mozilla/firefox/jur1232x.default/Cache/508D9754d01
.mozilla/firefox/jur1232x.default/Cache/50AF9776d01
.mozilla/firefox/jur1232x.default/Cache/50F108C1d01
.mozilla/firefox/jur1232x.default/Cache/52B97A7Fd01
.mozilla/firefox/jur1232x.default/Cache/5559C293d01
.mozilla/firefox/jur1232x.default/Cache/558DA761d01
.mozilla/firefox/jur1232x.default/Cache/568DF732d01
.mozilla/firefox/jur1232x.default/Cache/56AC4320d01
.mozilla/firefox/jur1232x.default/Cache/56AFF710d01
.mozilla/firefox/jur1232x.default/Cache/598878C6d01
.mozilla/firefox/jur1232x.default/Cache/5F8CE62Bd01
.mozilla/firefox/jur1232x.default/Cache/5FAEE609d01
.mozilla/firefox/jur1232x.default/Cache/618E6495d01
.mozilla/firefox/jur1232x.default/Cache/628EB446d01
.mozilla/firefox/jur1232x.default/Cache/645E105Bd01
.mozilla/firefox/jur1232x.default/Cache/6565381Ed01
.mozilla/firefox/jur1232x.default/Cache/66ACF420d01
.mozilla/firefox/jur1232x.default/Cache/678EC433d01
.mozilla/firefox/jur1232x.default/Cache/6A5282DEd01
.mozilla/firefox/jur1232x.default/Cache/6B244F2Bd01
.mozilla/firefox/jur1232x.default/Cache/71AD65A7d01
.mozilla/firefox/jur1232x.default/Cache/72ADB574d01
.mozilla/firefox/jur1232x.default/Cache/738F8567d01
.mozilla/firefox/jur1232x.default/Cache/746D2D15d01
.mozilla/firefox/jur1232x.default/Cache/748FD530d01
.mozilla/firefox/jur1232x.default/Cache/77ADC501d01
.mozilla/firefox/jur1232x.default/Cache/7B725E9Cd01
.mozilla/firefox/jur1232x.default/Cache/7E8F759Ad01
.mozilla/firefox/jur1232x.default/Cache/815E62B1d01
.mozilla/firefox/jur1232x.default/Cache/874CC217d01
.mozilla/firefox/jur1232x.default/Cache/8EA6FC51d01
.mozilla/firefox/jur1232x.default/Cache/8FF982D3d01
.mozilla/firefox/jur1232x.default/Cache/934D8343d01
.mozilla/firefox/jur1232x.default/Cache/944DD314d01
.mozilla/firefox/jur1232x.default/Cache/9A01E15Cd01
.mozilla/firefox/jur1232x.default/Cache/9A49F063d01
.mozilla/firefox/jur1232x.default/Cache/9E4D73BEd01
.mozilla/firefox/jur1232x.default/Cache/9E513796d01
.mozilla/firefox/jur1232x.default/Cache/A04E9060d01
.mozilla/firefox/jur1232x.default/Cache/A2040EB3d01
.mozilla/firefox/jur1232x.default/Cache/A2738B67d01
.mozilla/firefox/jur1232x.default/Cache/A54EA055d01
.mozilla/firefox/jur1232x.default/Cache/A64EF006d01
.mozilla/firefox/jur1232x.default/Cache/ADD4146Cd01
.mozilla/firefox/jur1232x.default/Cache/AF27EA6Fd01
.mozilla/firefox/jur1232x.default/Cache/AF4DE31Fd01
.mozilla/firefox/jur1232x.default/Cache/B0C14C19d01
.mozilla/firefox/jur1232x.default/Cache/B14F6181d01
.mozilla/firefox/jur1232x.default/Cache/B289FAB9d01
.mozilla/firefox/jur1232x.default/Cache/B2B2BB11d01
.mozilla/firefox/jur1232x.default/Cache/B705E911d01
.mozilla/firefox/jur1232x.default/Cache/B74FC127d01
.mozilla/firefox/jur1232x.default/Cache/B96BE256d01
.mozilla/firefox/jur1232x.default/Cache/BFBD2A22d01
.mozilla/firefox/jur1232x.default/Cache/C1A857BEd01
.mozilla/firefox/jur1232x.default/Cache/C1F1E14Bd01
.mozilla/firefox/jur1232x.default/Cache/C20D8BD4d01
.mozilla/firefox/jur1232x.default/Cache/C31E5C69d01
.mozilla/firefox/jur1232x.default/Cache/C4FE5F6Bd01
.mozilla/firefox/jur1232x.default/Cache/C5D1AF1Ed01
.mozilla/firefox/jur1232x.default/Cache/C5FD299Dd01
.mozilla/firefox/jur1232x.default/Cache/C5FFF5CFd01
.mozilla/firefox/jur1232x.default/Cache/C8DF506Cd01
.mozilla/firefox/jur1232x.default/Cache/CCAB716Fd01
.mozilla/firefox/jur1232x.default/Cache/CE50F491d01
.mozilla/firefox/jur1232x.default/Cache/D1515A55d01
.mozilla/firefox/jur1232x.default/Cache/D4D7DE0Dd01
.mozilla/firefox/jur1232x.default/Cache/DA2A5DC5d01
.mozilla/firefox/jur1232x.default/Cache/DBF40ECEd01
.mozilla/firefox/jur1232x.default/Cache/DC4EF771d01
.mozilla/firefox/jur1232x.default/Cache/EF8FE49Ad01
.mozilla/firefox/jur1232x.default/Cache/_CACHE_001_
.mozilla/firefox/jur1232x.default/Cache/_CACHE_002_
.mozilla/firefox/jur1232x.default/Cache/_CACHE_003_
.mozilla/firefox/jur1232x.default/Cache/_CACHE_MAP_
.nautilus/metafiles/burn:%2F%2F%2F.xml
.nautilus/metafiles/file:%2F%2F%2Fhome%2Fgarrett%2FDesktop%2Fsalvaged.xml
.nautilus/metafiles/file:%2F%2F%2Fhome%2Fgarrett%2FDesktop.xml
.nautilus/metafiles/x-nautilus-desktop:%2F%2F%2F.xml
skipping non-regular file ".openoffice.org2/user/config/arrowhd_en-GB.soe"
skipping non-regular file ".openoffice.org2/user/config/arrowhd_en-US_en-ZA.soe"
skipping non-regular file ".openoffice.org2/user/config/classic_en-GB.sog"
skipping non-regular file ".openoffice.org2/user/config/classic_en-US_en-ZA.sog"
skipping non-regular file ".openoffice.org2/user/config/hatching_en-GB.soh"
skipping non-regular file ".openoffice.org2/user/config/hatching_en-US_en-ZA.soh"
skipping non-regular file ".openoffice.org2/user/config/modern_en-GB.sog"
skipping non-regular file ".openoffice.org2/user/config/modern_en-US_en-ZA.sog"
skipping non-regular file ".openoffice.org2/user/config/palette_en-GB.soc"
skipping non-regular file ".openoffice.org2/user/config/palette_en-US_en-ZA.soc"
skipping non-regular file ".openoffice.org2/user/config/styles_en-GB.sod"
skipping non-regular file ".openoffice.org2/user/config/styles_en-US_en-ZA.sod"
.openoffice.org2/user/psprint/pspfontcache
.openoffice.org2/user/registry/cache/org.openoffice.Office.Addons.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Calc.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Commands.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Common.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Compatibility.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Events.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Impress.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Jobs.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Linguistic.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Paths.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.ProtocolHandler.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Recovery.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.SFX.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Substitution.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.TabBrowse.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.TypeDetection.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.Controller.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.Factories.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.GenericCommands.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.GlobalSettings.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.WriterCommands.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.WriterWindowState.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.UI.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Views.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.Writer.dat
.openoffice.org2/user/registry/cache/org.openoffice.Office.WriterWeb.dat
.openoffice.org2/user/registry/cache/org.openoffice.Setup.dat
.openoffice.org2/user/registry/cache/org.openoffice.System.dat
.openoffice.org2/user/registry/cache/org.openoffice.TypeDetection.Filter.dat
.openoffice.org2/user/registry/cache/org.openoffice.TypeDetection.Misc.dat
.openoffice.org2/user/registry/cache/org.openoffice.TypeDetection.Types.dat
.openoffice.org2/user/registry/cache/org.openoffice.VCL.dat
.openoffice.org2/user/registry/cache/org.openoffice.ucb.Configuration.dat
.openoffice.org2/user/registry/cache/org.openoffice.ucb.Store.dat
.openoffice.org2/user/registry/data/org/openoffice/Setup.xcu
.openoffice.org2/user/registry/data/org/openoffice/Office/Common.xcu
.openoffice.org2/user/registry/data/org/openoffice/Office/Recovery.xcu
.openoffice.org2/user/registry/data/org/openoffice/Office/Views.xcu
.openoffice.org2/user/uno_packages/cache/log.txt
.openoffice.org2/user/uno_packages/cache/stamp.sys
.openoffice.org2/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/Linux_x86rc
.openoffice.org2/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/unorc
.openoffice.org2/user/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend/
.openoffice.org2/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/
.purple/accels
.purple/accounts.xml
.purple/blist.xml
.purple/prefs.xml
.purple/status.xml
.purple/icons/01e1a8d4e13a85d35a784ca2d4a21ad3cf728a0a.jpg
.purple/icons/da56df8dd218a234c3f9069dc8a9993f91425b7d.jpg
.purple/logs/aim/rpg405/faryanheit212/2008-05-05.220905-0500CDT.txt
.purple/logs/aim/rpg405/kewii123/2008-05-05.173408-0500CDT.txt
.purple/logs/aim/rpg405/mikejamesirony/2008-05-05.221659-0500CDT.txt
.purple/logs/aim/rpg405/seanbadnt/2008-05-05.171755-0500CDT.txt
.purple/logs/aim/rpg405/surrendertheenow/2008-05-05.215635-0500CDT.txt
.tomboy/014770b6-6404-4eff-ba99-94b4cad71762.note
.tomboy/573b69f5-4d25-40c1-a6d7-ad0468758155.note
.tomboy/c117459e-2af4-4462-b684-a2aa46d0f6e3.note
.tomboy/c9294ac8-ca36-40a0-b7f1-8ffef4fb1600.note
.tomboy/addin-db-001/host-index
.tomboy/addin-db-001/addin-data/1/Tomboy.Tomboy,0.10.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.BacklinksAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.BugzillaAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.EvolutionAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.ExportToHtmlAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.FileSystemSyncServiceAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.FixedWidthAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.InsertTimestampAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.NoteOfTheDayAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.PrintNotesAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.SshSyncServiceAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.StickyNoteImportAddin,0.1.maddin
.tomboy/addin-db-001/addin-data/global/Tomboy.WebDavSyncServiceAddin,0.1.maddin
.tomboy/addin-db-001/addin-dir-data/usr_lib_tomboy_addins_b07dc18e.data
.tomboy/addin-db-001/addin-dir-data/usr_lib_tomboy_c760bb4e.data
.tomboy/addins/Tomboy.addins
.update-notifier/hooks_seen
.wapi/shared_data-garrett-desktop-Linux-i686-312-11-0
.wapi/shared_fileshare-garrett-desktop-Linux-i686-36-11-0
skipping non-regular file ".wine/dosdevices/c:"
skipping non-regular file ".wine/dosdevices/d:"
skipping non-regular file ".wine/dosdevices/d::"
skipping non-regular file ".wine/dosdevices/e:"
skipping non-regular file ".wine/dosdevices/e::"
skipping non-regular file ".wine/dosdevices/f:"
skipping non-regular file ".wine/dosdevices/f::"
skipping non-regular file ".wine/dosdevices/g:"
skipping non-regular file ".wine/dosdevices/g::"
skipping non-regular file ".wine/dosdevices/h:"
skipping non-regular file ".wine/dosdevices/h::"
skipping non-regular file ".wine/dosdevices/z:"
skipping non-regular file ".wine/drive_c/windows/notepad.exe"
skipping non-regular file ".wine/drive_c/windows/regedit.exe"
skipping non-regular file ".wine/drive_c/windows/rundll32.exe"
skipping non-regular file ".wine/drive_c/windows/uninstall.exe"
skipping non-regular file ".wine/drive_c/windows/winebrowser.exe"
skipping non-regular file ".wine/drive_c/windows/winhelp.exe"
skipping non-regular file ".wine/drive_c/windows/winhlp32.exe"
skipping non-regular file ".wine/drive_c/windows/command/start.exe"
skipping non-regular file ".wine/drive_c/windows/profiles/garrett/Desktop"
skipping non-regular file ".wine/drive_c/windows/profiles/garrett/My Documents"
skipping non-regular file ".wine/drive_c/windows/profiles/garrett/My Music"
skipping non-regular file ".wine/drive_c/windows/profiles/garrett/My Pictures"
skipping non-regular file ".wine/drive_c/windows/profiles/garrett/My Video"
skipping non-regular file ".wine/drive_c/windows/system32/control.exe"
skipping non-regular file ".wine/drive_c/windows/system32/help.exe"
skipping non-regular file ".wine/drive_c/windows/system32/msiexec.exe"
skipping non-regular file ".wine/drive_c/windows/system32/notepad.exe"
skipping non-regular file ".wine/drive_c/windows/system32/progman.exe"
skipping non-regular file ".wine/drive_c/windows/system32/regsvr32.exe"
skipping non-regular file ".wine/drive_c/windows/system32/wcmd.exe"
skipping non-regular file ".wine/drive_c/windows/system32/winmine.exe"
skipping non-regular file ".wine/drive_c/windows/system32/winver.exe"
.xine/catalog.cache
Desktop/MiniPE.v2k5.09.03-XT_21_APR_2008.rar
Desktop/MiniPE.v2k5.09.03-XT_UPDATED.ISO
Desktop/miniPE.AV.Update.2oo8.o4.25.rar
Desktop/ubuntu-8.04-alternate-i386.iso
Desktop/salvaged/
Desktop/salvaged/AFBR.lxf
Desktop/salvaged/Helvetica Neue LT Std Font.zip
Desktop/salvaged/bookmarks.html
Desktop/salvaged/faryanmobo.txt
Desktop/salvaged/AlphaSim - New Collection/
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/AlphaSim - SR-71 Blackbird.rar
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/AlphaSim - SR-71 Blackbird/
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/AlphaSim - SR-71 Blackbird/Effects/
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/AlphaSim - SR-71 Blackbird/Effects/texture/
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/AlphaSim - SR-71 Blackbird/SimObjects/
Desktop/salvaged/AlphaSim - New Collection/AlphaSim - SR-71 Blackbird (FSX)/AlphaSim - SR-71 Blackbird/SimObjects/Airplanes/
Desktop/salvaged/Flight Simulator X Files/
Desktop/salvaged/Flight Simulator X Files/747 going fast.FSR
Desktop/salvaged/Flight Simulator X Files/ACL Flight Trip Save Point.FLT
Desktop/salvaged/Flight Simulator X Files/ACL Flight Trip Save Point.FSSAVE
Desktop/salvaged/Flight Simulator X Files/ACL Flight Trip Save Point.WX
Desktop/salvaged/Flight Simulator X Files/BBird at CHI.FLT
Desktop/salvaged/Flight Simulator X Files/BBird at CHI.FSSAVE
Desktop/salvaged/Flight Simulator X Files/BBird at CHI.WX
Desktop/salvaged/Flight Simulator X Files/Cold & Dark Southwest at KMDW.FLT
Desktop/salvaged/Flight Simulator X Files/Cold & Dark Southwest at KMDW.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Cold & Dark Southwest at KMDW.WX
Desktop/salvaged/Flight Simulator X Files/Executive Hopping.FLT
Desktop/salvaged/Flight Simulator X Files/Executive Hopping.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Executive Hopping.WX
Desktop/salvaged/Flight Simulator X Files/Hawaii flight hopping.FLT
Desktop/salvaged/Flight Simulator X Files/Hawaii flight hopping.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Hawaii flight hopping.WX
Desktop/salvaged/Flight Simulator X Files/IFR Albertus to Chicago Midway Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Chicago-O'Hare Intl to Ft Lauderdale-Hollywood Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Chicago-O'Hare Intl to Hong Kong Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Chicago-O'Hare Intl to McCarran Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Clark to Chicago-O'Hare Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Cleveland-Hopkins Intl to Chicago-O'Hare Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Du Page to Foster.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Dubuque Regl to Palwaukee Mun.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Foster to Chicago Midway Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Foster to Du Page.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Foster to Palwaukee Mun.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Gregorio Luperon Intl to Frankfurt Main.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Kona Intl At Keahole to Honolulu Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR McCarran Intl to Chicago Midway Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Molokai to Kona Intl At Keahole.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Orlando Intl to Melbourne Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Palwaukee Mun to Cleveland-Hopkins Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Palwaukee Mun to Dubuque Regl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Stevens Anchorage Intl to Hong Kong Intl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Washington Dulles Intl to Ronald Reagan Washington Natl.PLN
Desktop/salvaged/Flight Simulator X Files/IFR Zama Lake to Stevens Anchorage Intl.PLN
Desktop/salvaged/Flight Simulator X Files/KORD to Hong Kong.FLT
Desktop/salvaged/Flight Simulator X Files/KORD to Hong Kong.FSSAVE
Desktop/salvaged/Flight Simulator X Files/KORD to Hong Kong.WX
Desktop/salvaged/Flight Simulator X Files/Lear 45 Executive.FLT
Desktop/salvaged/Flight Simulator X Files/Lear 45 Executive.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Lear 45 Executive.WX
Desktop/salvaged/Flight Simulator X Files/Logbook.BIN
Desktop/salvaged/Flight Simulator X Files/Low Pass Tower at ORD.FSR
Desktop/salvaged/Flight Simulator X Files/PMDG 747-400FX Cold & Dark - KPAE.FLT
Desktop/salvaged/Flight Simulator X Files/PMDG 747-400FX Cold & Dark - KPAE.FSSAVE
Desktop/salvaged/Flight Simulator X Files/PMDG 747-400FX Cold & Dark - KPAE.WX
Desktop/salvaged/Flight Simulator X Files/PMDG 747-400X Cold & Dark - KPAE.FLT
Desktop/salvaged/Flight Simulator X Files/PMDG 747-400X Cold & Dark - KPAE.FSSAVE
Desktop/salvaged/Flight Simulator X Files/PMDG 747-400X Cold & Dark - KPAE.WX
Desktop/salvaged/Flight Simulator X Files/Palwaukee Flyers.FLT
Desktop/salvaged/Flight Simulator X Files/Palwaukee Flyers.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Palwaukee Flyers.WX
Desktop/salvaged/Flight Simulator X Files/Previous Flight.FLT
Desktop/salvaged/Flight Simulator X Files/Previous Flight.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Previous Flight.WX
Desktop/salvaged/Flight Simulator X Files/Southwest Airlines.FLT
Desktop/salvaged/Flight Simulator X Files/Southwest Airlines.FSSAVE
Desktop/salvaged/Flight Simulator X Files/Southwest Airlines.WX
Desktop/salvaged/Flight Simulator X Files/VFR Palwaukee Mun to Brookeridge Air Park.PLN
Desktop/salvaged/Flight Simulator X Files/hi carrier.FLT
Desktop/salvaged/Flight Simulator X Files/hi carrier.FSSAVE
Desktop/salvaged/Flight Simulator X Files/hi carrier.SPB
Desktop/salvaged/Flight Simulator X Files/hi carrier.WX
Desktop/salvaged/Flight Simulator X Pics/
Desktop/salvaged/Flight Simulator X Pics/2008-2-18_12-33-34-968.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-19_20-0-10-859.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-19_20-40-46-687.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-24_14-32-7-718.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-27_17-9-4-921.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-29_21-9-20-453.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-29_21-9-34-125.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-2-29_21-9-46-859.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-3-25_22-45-38-955.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-3-30_20-10-0-515.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-3-30_20-10-17-453.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-3-30_20-5-12-31.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-3-30_20-6-6-375.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-15_18-13-33-594.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-15_18-13-48-657.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-15_18-14-5-985.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-15_18-15-14-2.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-15_18-15-34-33.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-15_18-15-5-751.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-16_20-31-18-328.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-16_20-31-22-156.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-16_20-31-30-890.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-16_20-31-43-125.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-16_20-38-53-562.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-1_18-26-46-630.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-1_18-26-54-865.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-1_18-8-30-574.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-1_18-8-41-716.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-1_20-11-51-268.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-1_20-12-0-424.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-22_16-49-51-879.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-23_17-28-11-203.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-24_21-8-5-875.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-30_18-42-50-234.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-4_15-45-19-0.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-4_15-45-7-281.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-4_18-11-35-515.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-4_18-11-42-125.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-4_18-11-48-531.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-4_18-5-11-125.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-5_11-27-2-578.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-4-5_12-34-40-859.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-1_21-7-36-0.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-2_15-54-33-906.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-2_15-59-12-203.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-2_15-59-2-421.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-2_20-43-16-500.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-2_20-43-7-546.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-3_22-9-4-312.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_12-41-35-875.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_12-41-6-296.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_15-24-14-203.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_15-24-2-750.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_15-7-26-968.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_15-7-40-562.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_21-19-53-875.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_21-25-44-781.BMP
Desktop/salvaged/Flight Simulator X Pics/2008-5-4_21-25-53-375.BMP
Desktop/salvaged/Flight Simulator X Pics/Thumbs.db
Desktop/salvaged/Flight Simulator X Pics/crj-900gate.jpg
Desktop/salvaged/Flight Simulator X Pics/inverted_cessna.jpg
Desktop/salvaged/Flight Simulator X Pics/swa_dusk.jpg
Desktop/salvaged/Flight Simulator X Pics/swa_dusk2.jpg
Desktop/salvaged/Flight Simulator X Pics/swa_dusk3.jpg
Desktop/salvaged/Flight Simulator X Pics/swair.jpg
Desktop/salvaged/ZAU Files/
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/C90 PRO Resurrection v1.sct
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/C90 PRO Resurrection v2.sct2
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/Letter of Agreement between Chicago Center and C90 TRACON.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/Letter of Agreement between Chicago Center and Milwaukee TRACON.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/Letter of Agreement between Chicago TRACON and Milwaukee TRACON.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ORD Runway Config Template.txt
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ZAU Alias.txt
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ZAU Pro Resurrection v1.0.rwy
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ZAU Pro Resurrection v1.0.sct
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ZAU Pro Resurrection v1.1.rwy
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ZAU Pro Resurrection v1.1.sct
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/ZAU V4.pof
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 1 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 2 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 3 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 4 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 5 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 6 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 7 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 8 SOP.pdf
Desktop/salvaged/ZAU Files/ZAU Sector File, Alias, POF, LOAs/SOP's/ZAU Ch. 9 SOP.pdf
Momentum Studios/Grade8Scans/scanreport.txt
Momentum Studios/Grade8Scans/Events/confirmation/IMG_0592.jpg
Momentum Studios/Grade8Scans/Events/confirmation/IMG_0593.jpg
Momentum Studios/Grade8Scans/Events/confirmation/IMG_0601.jpg
Momentum Studios/Grade8Scans/Events/confirmation/IMG_0602.jpg
Momentum Studios/Grade8Scans/Events/confirmation/IMG_0616.jpg
Momentum Studios/Grade8Scans/Events/confirmation/IMG_0619.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0440.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0444.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0455.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0461.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0470.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0475.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0480.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0483.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0484.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0488.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0489.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0502.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0506.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0508.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0510.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0512.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0516.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0520.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0524.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0535.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0536.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0544.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0545.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0550.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0555.jpg
Momentum Studios/Grade8Scans/Events/play pics/IMG_0559.jpg
My Pictures/Introductory Flight/DSC00312.JPG
My Pictures/Introductory Flight/DSC00313.JPG
My Pictures/Introductory Flight/DSC00314.JPG
My Pictures/Introductory Flight/DSC00315.JPG
My Pictures/Introductory Flight/DSC00318.JPG
My Pictures/Introductory Flight/DSC00320.JPG
My Pictures/Introductory Flight/DSC00322.JPG
My Pictures/Introductory Flight/DSC00323.JPG
My Pictures/Introductory Flight/DSC00324.JPG
My Pictures/Introductory Flight/DSC00327.JPG
My Pictures/Introductory Flight/DSC00328.JPG
My Pictures/Introductory Flight/DSC00329.JPG
My Pictures/Introductory Flight/DSC00330.JPG
My Pictures/Introductory Flight/DSC00331.JPG
My Pictures/Introductory Flight/DSC00332.JPG
My Pictures/Introductory Flight/DSC00333.JPG
My Pictures/Introductory Flight/DSC00334.JPG
My Pictures/Introductory Flight/DSC00336.JPG
My Pictures/Introductory Flight/DSC00337.JPG
My Pictures/Introductory Flight/DSC00338.JPG
My Pictures/Introductory Flight/DSC00339.JPG
My Pictures/Introductory Flight/DSC00341.JPG
My Pictures/Introductory Flight/DSC00342.JPG
My Pictures/Introductory Flight/DSC00344.JPG
My Pictures/Introductory Flight/Thumbs.db
My Pictures/Science Olympiad State 2008/124702.jpg
My Pictures/Science Olympiad State 2008/124713.jpg
My Pictures/Science Olympiad State 2008/124725.jpg
My Pictures/Science Olympiad State 2008/160946.jpg
My Pictures/Science Olympiad State 2008/220924.jpg
My Pictures/Science Olympiad State 2008/DSC02290.JPG
My Pictures/Science Olympiad State 2008/DSC02293.JPG
My Pictures/Science Olympiad State 2008/DSC02294.JPG
My Pictures/Science Olympiad State 2008/DSC02295.JPG
My Pictures/Science Olympiad State 2008/DSC02296.JPG
My Pictures/Science Olympiad State 2008/DSC02297.JPG
My Pictures/Science Olympiad State 2008/DSC02298.JPG
My Pictures/Science Olympiad State 2008/DSC02299.JPG
My Pictures/Science Olympiad State 2008/DSC02300.JPG
My Pictures/Science Olympiad State 2008/DSC02301.JPG
My Pictures/Science Olympiad State 2008/DSC02302.JPG
My Pictures/Science Olympiad State 2008/DSC02303.JPG
My Pictures/Science Olympiad State 2008/DSC02304.JPG
My Pictures/Science Olympiad State 2008/DSC02305.JPG
My Pictures/Science Olympiad State 2008/DSC02306.JPG
My Pictures/Science Olympiad State 2008/DSC02307.JPG
My Pictures/Science Olympiad State 2008/DSC02308.JPG
My Pictures/Science Olympiad State 2008/DSC02309.JPG
My Pictures/Science Olympiad State 2008/DSC02310.JPG
My Pictures/Science Olympiad State 2008/DSC02311.JPG
My Pictures/Science Olympiad State 2008/DSC02312.JPG
My Pictures/Science Olympiad State 2008/DSC02313.JPG
My Pictures/Science Olympiad State 2008/DSC02314.JPG
My Pictures/Science Olympiad State 2008/DSC02315.JPG
My Pictures/Science Olympiad State 2008/DSC02316.JPG
My Pictures/Science Olympiad State 2008/DSC02317.JPG
My Pictures/Science Olympiad State 2008/DSC02318.JPG
My Pictures/Science Olympiad State 2008/DSC02319.JPG
My Pictures/Science Olympiad State 2008/DSC02320.JPG
My Pictures/Science Olympiad State 2008/DSC02321.JPG
My Pictures/Science Olympiad State 2008/DSC02322.JPG
My Pictures/Science Olympiad State 2008/DSC02323.JPG
My Pictures/Science Olympiad State 2008/DSC02324.JPG
My Pictures/Science Olympiad State 2008/DSC02325.JPG
My Pictures/Science Olympiad State 2008/DSC02326.JPG
My Pictures/Science Olympiad State 2008/DSC02327.JPG
My Pictures/Science Olympiad State 2008/DSC02328.JPG
My Pictures/Science Olympiad State 2008/DSC02329.JPG
My Pictures/Science Olympiad State 2008/DSC02330.JPG
My Pictures/Science Olympiad State 2008/DSC02331.JPG
My Pictures/Science Olympiad State 2008/DSC02332.JPG
My Pictures/Science Olympiad State 2008/DSC02333.JPG
My Pictures/Science Olympiad State 2008/DSC02334.JPG
My Pictures/Science Olympiad State 2008/DSC02335.JPG
My Pictures/Science Olympiad State 2008/DSC02336.JPG
My Pictures/Science Olympiad State 2008/DSC02337.JPG
My Pictures/Science Olympiad State 2008/DSC02338.JPG
My Pictures/Science Olympiad State 2008/DSC02339.JPG
My Pictures/Science Olympiad State 2008/DSC02340.JPG
My Pictures/Science Olympiad State 2008/DSC02341.JPG
My Pictures/Science Olympiad State 2008/DSC02342.JPG
My Pictures/Science Olympiad State 2008/DSC02345.JPG
My Pictures/Science Olympiad State 2008/DSC02347.JPG
My Pictures/Science Olympiad State 2008/DSC02348.JPG
My Pictures/Science Olympiad State 2008/DSC02349.JPG
My Pictures/Science Olympiad State 2008/DSC02350.JPG
My Pictures/Science Olympiad State 2008/DSC02351.JPG
My Pictures/Science Olympiad State 2008/DSC02352.JPG
My Pictures/Science Olympiad State 2008/DSC02353.JPG
My Pictures/Science Olympiad State 2008/DSC02355.JPG
My Pictures/Science Olympiad State 2008/DSC02356.JPG
My Pictures/Science Olympiad State 2008/DSC02357.JPG
My Pictures/Science Olympiad State 2008/DSC02358.JPG
My Pictures/Science Olympiad State 2008/DSC02359.JPG
My Pictures/Science Olympiad State 2008/DSC02360.JPG
My Pictures/Science Olympiad State 2008/DSC02361.JPG
My Pictures/Science Olympiad State 2008/DSC02362.JPG
My Pictures/Science Olympiad State 2008/DSC02363.JPG
My Pictures/Science Olympiad State 2008/DSC02365.JPG
My Pictures/Science Olympiad State 2008/DSC02366.JPG
My Pictures/Science Olympiad State 2008/DSC02367.JPG
My Pictures/Science Olympiad State 2008/DSC02368.JPG
My Pictures/Science Olympiad State 2008/DSC02369.JPG
My Pictures/Science Olympiad State 2008/DSC02370.JPG
My Pictures/Science Olympiad State 2008/DSC02371.JPG
My Pictures/Science Olympiad State 2008/DSC02372.JPG
My Pictures/Science Olympiad State 2008/DSC02374.JPG
My Pictures/Science Olympiad State 2008/DSC02381.JPG
My Pictures/Science Olympiad State 2008/DSC02382.JPG
My Pictures/Science Olympiad State 2008/DSC02383.JPG
My Pictures/Science Olympiad State 2008/DSC02384.JPG
My Pictures/Science Olympiad State 2008/DSC02385.JPG
My Pictures/Science Olympiad State 2008/DSC02386.JPG
My Pictures/Science Olympiad State 2008/DSC02387.JPG
My Pictures/Science Olympiad State 2008/DSC02390.JPG
My Pictures/Science Olympiad State 2008/DSC02391.JPG
My Pictures/Science Olympiad State 2008/DSC02393.JPG
My Pictures/Science Olympiad State 2008/DSC02394.JPG
My Pictures/Science Olympiad State 2008/DSC02395.JPG
My Pictures/Science Olympiad State 2008/DSC02396.JPG
My Pictures/Science Olympiad State 2008/DSC02398.JPG
My Pictures/Science Olympiad State 2008/DSC02399.JPG
My Pictures/Science Olympiad State 2008/DSC02400.JPG
My Pictures/Science Olympiad State 2008/DSC02401.JPG
My Pictures/Science Olympiad State 2008/DSC02402.JPG
My Pictures/Science Olympiad State 2008/DSC02403.JPG
My Pictures/Science Olympiad State 2008/DSC02404.JPG
My Pictures/Science Olympiad State 2008/DSC02405.JPG
My Pictures/Science Olympiad State 2008/DSC02406.JPG
My Pictures/Science Olympiad State 2008/DSC02407.JPG
My Pictures/Science Olympiad State 2008/DSC02408.JPG
My Pictures/Science Olympiad State 2008/DSC02409.JPG
My Pictures/Science Olympiad State 2008/DSC02410.JPG
My Pictures/Science Olympiad State 2008/DSC02411.JPG
My Pictures/Science Olympiad State 2008/DSC02412.JPG
My Pictures/Science Olympiad State 2008/DSC02413.JPG
My Pictures/Science Olympiad State 2008/DSC02414.JPG
My Pictures/Science Olympiad State 2008/DSC02417.JPG
My Pictures/Science Olympiad State 2008/DSC02419.JPG
My Pictures/Science Olympiad State 2008/DSC02421.JPG
My Pictures/Science Olympiad State 2008/DSC02426.JPG
My Pictures/Science Olympiad State 2008/IMG_0026.JPG
My Pictures/Science Olympiad State 2008/IMG_0033.JPG
My Pictures/Science Olympiad State 2008/IMG_0034.JPG
My Pictures/Science Olympiad State 2008/IMG_0035.JPG
My Pictures/Science Olympiad State 2008/IMG_0036.JPG
My Pictures/Science Olympiad State 2008/IMG_0037.JPG
My Pictures/Science Olympiad State 2008/IMG_0038.JPG
My Pictures/Science Olympiad State 2008/IMG_0039.JPG
My Pictures/Science Olympiad State 2008/IMG_0040.JPG
My Pictures/Science Olympiad State 2008/IMG_0041.JPG
My Pictures/Science Olympiad State 2008/IMG_0042.JPG
My Pictures/Science Olympiad State 2008/IMG_0043.JPG
My Pictures/Science Olympiad State 2008/IMG_0044.JPG
My Pictures/Science Olympiad State 2008/IMG_0046.JPG
My Pictures/Science Olympiad State 2008/IMG_0049.JPG
My Pictures/Science Olympiad State 2008/IMG_0050.JPG
My Pictures/Science Olympiad State 2008/IMG_0051.JPG
My Pictures/Science Olympiad State 2008/IMG_0052.JPG
My Pictures/Science Olympiad State 2008/IMG_0053.JPG
My Pictures/Science Olympiad State 2008/MOV02388.MPG
My Pictures/Science Olympiad State 2008/MOV02397.MPG
My Pictures/Science Olympiad State 2008/MVI_0027.mpg
My Pictures/Science Olympiad State 2008/Thumbs.db
Shared/10 The Bad Touch.mp3
skipping non-regular file "Websites/My Flash"

Number of files: 62924
Number of files transferred: 1259
Total file size: 97784790600 bytes
Total transferred file size: 3397414491 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 1641274
File list generation time: 1.024 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 1649090
Total bytes received: 7820

sent 1649090 bytes  received 7820 bytes  1104606.67 bytes/sec
total size is 97784790600  speedup is 59016.36
```

That works without halting the system, but when performing the actual transfer, it locks up the system.

---

### Post by mannheim on 2008-05-06
Just a thought: have you checked you are not running out of disk space (on ~/ or on /media/sdc1 or on the root partition)?

A related thought, perhaps once you ran rsync with /media/sdc1 accidentally not mounted, so that the rsync command was actually writing to the root device and not to the disk sdc1. This could have filled up your root partition.

---

### Post by RPG405 on 2008-05-06
I always run rsync with the -n option before I run it with the transfers, to see exactly what it is doing. There have been no times where I have run rsync without the disc mounted, or when writing to the root filesystem. If there had been, I would have cought it during the dry-run with the -n option.

---

### Post by wkulecz on 2008-05-13
No issues with rsync and 8.04 here. I've already used it to clone my installation on another computer.

using --delete is dangerous especially if there might be mount errors. The IO errors in your paste are worth looking into.

--wally.

---

### Post by sehe on 2008-05-27
are you by any chance backing up to USB drive? There is known equipment (USB hubs, certain drives that include their own) that choke on large packets. Especially when doing large backups, this can happen.

It is a very wellknown problem with some drives on vista too (vista SP contains a 'fix' - probably to limit the packet size artificially). I suggest you look into hardware problems (because lockups are usually *that*. No userland fuckup could disable your sysreq interrupt key)

---

### Post by bobstro on 2008-05-28
I don't see anything wrong with what you're trying to do. It certainly should work, and rsync should *not* be capable of locking up your system as you describe. I think you're on the right track with a possible hardware problem, or interaction with USB. Of course, the question is why it only started acting up after the upgrade.

One question: What filesystem is on sdc1? Is it possibly a non-native (NTFS?) filesystem? Perhaps different drivers are in play between Ubuntu versions. I have had some "oddities" using NTFS file systems, especially with different permissions and file naming conventions.

Also, definitely take a look at /var/log/syslog for any error messages that might yield a clue. Has a file system check been run on /dev/sdc1?

Good luck. Rsync is a wonderful tool, and I hate the idea of running without a good backup!

- Bob

---

### Post by RPG405 on 2008-07-22
I found the solution. The problem was a broken SATA controller on the motherboard. I switched motherboards and now everything works fine.

---

