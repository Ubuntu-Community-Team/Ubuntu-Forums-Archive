---
title: "rsync has become noisy"
date: 2009-05-02
forum: General Help
---

### Post by Dr Eigen on 2009-05-02
I regularly use rsync to transfer projects between two machines.

Recently (as in the last couple of days) when I rsync between two fully updated Hardy systems I get a heap of junk dumped to my terminal:

```
rsync --rsh=ssh --blocking-io -a -z --progress abc@XXX:'Grow_scripts/Rewrite/*f90' .
receiving incremental file list
server_sender starting pid=14789
[sender] make_file(bridgepoints.f90,*,0)
[sender] make_file(bumpiness.f90,*,0)
[sender] make_file(checkassign.f90,*,0)
[sender] make_file(cleancalcdata.f90,*,0)
[sender] make_file(control.f90,*,0)
[sender] make_file(coords.f90,*,0)
[sender] make_file(dertrans.f90,*,0)
[sender] make_file(dotbfinvert.f90,*,0)
[sender] make_file(dotbuckleeig.f90,*,0)
[sender] make_file(dotmakevecs.f90,*,0)
[sender] make_file(dynamicvectors.f90,*,0)
[sender] make_file(eigconfid.f90,*,0)
[sender] make_file(Energy.f90,*,0)
[sender] make_file(explore_distance.f90,*,0)
[sender] make_file(factorial.f90,*,0)
[sender] make_file(findwfn.f90,*,0)
[sender] make_file(finitederiv.f90,*,0)
[sender] make_file(flag_geoms.f90,*,0)
[sender] make_file(makeperms.f90,*,0)
[sender] make_file(mask_potfile.f90,*,0)
[sender] make_file(nullperms.f90,*,0)
[sender] make_file(objective_dummy.f90,*,0)
[sender] make_file(objective_perm.f90,*,0)
[sender] make_file(objective_rots.f90,*,0)
[sender] make_file(overlaps2dia.f90,*,0)
[sender] make_file(permassign.f90,*,0)
[sender] make_file(permutations.f90,*,0)
[sender] make_file(plotter.f90,*,0)
[sender] make_file(potfile.f90,*,0)
[sender] make_file(propagate.f90,*,0)
[sender] make_file(ptob.f90,*,0)
[sender] make_file(ptob-perm.f90,*,0)
[sender] make_file(report-setup.f90,*,0)
[sender] make_file(rotopt.f90,*,0)
[sender] make_file(safeopen.f90,*,0)
[sender] make_file(sanitize.f90,*,0)
[sender] make_file(saperms.f90,*,0)
[sender] make_file(scanpotfile.f90,*,0)
[sender] make_file(search.f90,*,0)
[sender] make_file(smoothness.f90,*,0)
[sender] make_file(sort.f90,*,0)
[sender] make_file(sv_test.f90,*,0)
[sender] make_file(system.f90,*,0)
[sender] make_file(transforms.f90,*,0)
[sender] make_file(weights.f90,*,0)
send_file_list done
send_files starting
send_files phase=1
send_files phase=2
send files finished
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 11 bytes  received 3205 bytes  2144.00 bytes/sec
total size is 153380  speedup is 47.69

```

Previously that would have been only the first and two last limes.

When I rsync from/to one of these machines to/from other, non-Ubuntu machines I get the expected three line output that I used to get between the Hardy boxes.

a)  Has anyone else experienced this?
b)  What is causing it?

---

### Post by andrew.46 on 2009-05-02
Hi Dr Eigen,

If you omit '--progress' does this fix the problem?

```
--progress              show progress during transfer
```

All the best,

Andrew

---

### Post by Dr Eigen on 2009-05-02
No, that doesn't fix anything.

As I have implied, all the noise is a *change* in behaviour with the same command line.

---

