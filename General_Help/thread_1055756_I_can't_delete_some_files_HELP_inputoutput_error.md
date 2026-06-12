---
title: "I can't delete some files HELP input/output error"
date: 2009-01-31
forum: General Help
---

### Post by Celeb on 2009-01-31
Hi encounter my self in a dilema... I install a game in my Windows partition, but in the midle of the instalation ( right on the copy the textures files to the disk ). So i try to delete them manualy and it gave my the usual windows CHAN.... so... i loged in my User and try:

joaquin@amanda:/media/disk/L2Dex/Lineage II$ sudo rm -rf Textures/
[sudo] password for joaquin: 
rm: cannot remove `Textures/Aden_GiantCave_T.utx': Input/output error
rm: cannot remove `Textures/Broken_coloseum_T.utx': Input/output error
rm: cannot remove `Textures/Dion_monster_sports_T.utx': Input/output error
rm: cannot remove `Textures/Dwarf_Bridge_T.utx': Input/output error
rm: cannot remove `Textures/Field_Deco_Artifact_T.utx': Input/output error
rm: cannot remove `Textures/Giran_antaras_t.utx': Input/output error
rm: cannot remove `Textures/Godad_Dragoncave_T.utx': Input/output error
rm: cannot remove `Textures/hellbound_02_T.utx': Input/output error
rm: cannot remove `Textures/Innadrill_V_T.utx': Input/output error
rm: cannot remove `Textures/L2_Cha_select.utx': Input/output error
rm: cannot remove `Textures/oren_hdt_part2_t.utx': Input/output error
rm: cannot remove `Textures/Oren_sporesea_T.utx': Input/output error
rm: cannot remove `Textures/Oren_tree_T.utx': Input/output error
rm: cannot remove `Textures/Oren_tx.utx': Input/output error
rm: cannot remove `Textures/Oren_V_T.utx': Input/output error
rm: cannot remove `Textures/Particles.utx': Input/output error
rm: cannot remove `Textures/phabel_karoncave_T.utx': Input/output error
rm: cannot remove `Textures/Primitive_FieldOBJ_T.utx': Input/output error
rm: cannot remove `Textures/Primitive_tree_T.utx': Input/output error
rm: cannot remove `Textures/PvPZone_T.utx': Input/output error
rm: cannot remove `Textures/Quest_worldcamp_T.utx': Input/output error
rm: cannot remove `Textures/rhion_orc_dungeon_t.utx': Input/output error
rm: cannot remove `Textures/RionSctgart_tree_T.utx': Input/output error
rm: cannot remove `Textures/Rion_Orc_Village_T.utx': Input/output error

So.. i try to rename them

mv: cannot stat `Textures/Aden_GiantCave_T.utx': Input/output error

I try to do the rm from the inode... nothing

This is an ls -loh

joaquin@amanda:/media/disk/L2Dex/Lineage II/Textures$ ls -loh
ls: cannot access Aden_GiantCave_T.utx: Input/output error
ls: cannot access Broken_coloseum_T.utx: Input/output error
ls: cannot access Dion_monster_sports_T.utx: Input/output error
ls: cannot access Dwarf_Bridge_T.utx: Input/output error
ls: cannot access Field_Deco_Artifact_T.utx: Input/output error
ls: cannot access Giran_antaras_t.utx: Input/output error
ls: cannot access Godad_Dragoncave_T.utx: Input/output error
ls: cannot access hellbound_02_T.utx: Input/output error
ls: cannot access Innadrill_V_T.utx: Input/output error
ls: cannot access L2_Cha_select.utx: Input/output error
ls: cannot access oren_hdt_part2_t.utx: Input/output error
ls: cannot access Oren_sporesea_T.utx: Input/output error
ls: cannot access Oren_tree_T.utx: Input/output error
ls: cannot access Oren_tx.utx: Input/output error
ls: cannot access Oren_V_T.utx: Input/output error
ls: cannot access Particles.utx: Input/output error
ls: cannot access phabel_karoncave_T.utx: Input/output error
ls: cannot access Primitive_FieldOBJ_T.utx: Input/output error
ls: cannot access Primitive_tree_T.utx: Input/output error
ls: cannot access PvPZone_T.utx: Input/output error
ls: cannot access Quest_worldcamp_T.utx: Input/output error
ls: cannot access rhion_orc_dungeon_t.utx: Input/output error
ls: cannot access RionSctgart_tree_T.utx: Input/output error
ls: cannot access Rion_Orc_Village_T.utx: Input/output error
total 0
-????????? ? ? ?                ? Aden_GiantCave_T.utx
-????????? ? ? ?                ? Broken_coloseum_T.utx
-????????? ? ? ?                ? Dion_monster_sports_T.utx
-????????? ? ? ?                ? Dwarf_Bridge_T.utx
-????????? ? ? ?                ? Field_Deco_Artifact_T.utx
-????????? ? ? ?                ? Giran_antaras_t.utx
-????????? ? ? ?                ? Godad_Dragoncave_T.utx
-????????? ? ? ?                ? hellbound_02_T.utx
-????????? ? ? ?                ? Innadrill_V_T.utx
-????????? ? ? ?                ? L2_Cha_select.utx
-????????? ? ? ?                ? oren_hdt_part2_t.utx
-????????? ? ? ?                ? Oren_sporesea_T.utx
-????????? ? ? ?                ? Oren_tree_T.utx
-????????? ? ? ?                ? Oren_tx.utx
-????????? ? ? ?                ? Oren_V_T.utx
-????????? ? ? ?                ? Particles.utx
-????????? ? ? ?                ? phabel_karoncave_T.utx
-????????? ? ? ?                ? Primitive_FieldOBJ_T.utx
-????????? ? ? ?                ? Primitive_tree_T.utx
-????????? ? ? ?                ? PvPZone_T.utx
-????????? ? ? ?                ? Quest_worldcamp_T.utx
-????????? ? ? ?                ? rhion_orc_dungeon_t.utx
-????????? ? ? ?                ? Rion_Orc_Village_T.utx
-????????? ? ? ?                ? RionSctgart_tree_T.utx


HELP... im runing out of ideas. At least some explenation

---

### Post by croto on 2009-01-31
el disco hecho crema? Wild guess no mas.

---

### Post by Celeb on 2009-02-04
Decis que tengo errores en el disco? Lo puedo recuperar haciendo un low level format?

---

### Post by croto on 2009-02-04
La verdad q no estoy seguro si hay errores fisicos o logicos en el disco... por ahi te conviene buscar alguna especie de checkdisk, o algo asi. Estoy en el laburo, vuelvo a la noche!

---

### Post by markonhawthorne on 2010-09-01
Solved!

I saw this today on an engineer's workstation where ls
shows stuff like this:

-????????? ? ? ? ? simple_getdata.c
-????????? ? ? ? ? dma_util
-????????? ? ? ? ? Dion_monster_sports_T.utx

This looks like corrupted filesystem inodes (the
data structure that contains information about files).
This is a very serious condition, and usually means
you're going to have to rebuild the filesystem.
It was caused by an errant DMA engine spewing data into the
filesystem.

I shut down Linux, booted single-user and ran "fsck -y"
(say yes to all questions; no reason not to).  It replied
that the journaled file systems were A-OK.  It wasn't.

So I looked up how to force a filesystem check, and that is
"touch /forcefsck; reboot".  This turned up MANY MANY errors
and placed several files in lost+found/ directory.

When we rebooted, the corrupt files were gone, some in
/lost+found/ and some missing entirely, but the filesystem
was functional again.  The problem is, many more files
throughout the filesystem could be missing, so we reformatted
the partition and went for backup tapes.

Mark Mason
Engineering Design Team

---

### Post by Prescilla on 2011-07-22
I have the same problem, I was in the middle of transferring some video files from my USB flash disk and Ubuntu just crashed. I am not sure if some of the files were transferred but after reboot all the files were transferred but it was corrupted.  I cannot rename nor remove it. I've tried rebooting several times and force fsck. I still cannot find a way to delete the files. Please help.

Here are the files:
-rwxrwxrwx 1 root root 367436186 2011-07-20 00:39 S05E14 - Parasite.avi
-????????? ? ?    ?            ?                ? Criminal Minds S05E15 - Public Enemy.avi
-????????? ? ?    ?            ?                ? Criminal Minds S05E15 - Public Enemy.srt
-????????? ? ?    ?            ?                ? Criminal Minds S05E16 - Mosley Lane.srt
-????????? ? ?    ?            ?                ? Criminal Minds S05E16 - Mo&#30224;ley Lane.avi
-????????? ? ?    ?            ?                ? Criminal Minds S05E17 - Solitary Man.avi
-????????? ? ?    ?            ?                ? Criminal Minds S05E17 - Solitary Man.s&#30224;t
-rwxrwxrwx 3 root root 367305940 2011-07-21 15:39 S05E20.HDTV.XviD-NoTV.[VTV].avi
-rwxrwxrwx 1 root root 367460352 2011-07-21 19:50 S05E21.HDTV.XviD-NoTV.[VTV].avi
-rwxrwxrwx 1 root root 367490936 2011-07-22 10:32 S05E22.The.Internet&#30224;Is.Forever.HDTV.XviD-FQM.[VTV].avi
-rwxrwxrwx 1 root root 367434956 2011-07-21 11:09 Criminal.Minds.S05E23.Our.Darkest.Hour.HDTV.XviD-FQM.[VTV].avi
-rwxrwxrwx 1 root root     57311 2010-10-20 15:31 Criminal Minds S05&#30224;14 - Parasite.srt

---

