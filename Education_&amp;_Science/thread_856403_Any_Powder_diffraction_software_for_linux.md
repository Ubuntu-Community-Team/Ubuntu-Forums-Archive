---
title: "Any Powder diffraction software for linux?"
date: 2008-07-11
forum: Education &amp; Science
---

### Post by Miguel on 2008-07-11
Dear ubunteros,

I'm interested on calculating some powder diffraction spectra, to compare some structures I get at high pressure with experimental patterns. I've been looking for a couple of days for powder diffraction software, and EXPO was the only thing I could find. However, I didn't really see how to download it, and furthermore the software seemed pretty old. Yes, I know the Rietveld method hasn't changed much in the last 50 years but, you know, GTk and Qt have. 

Anyway, does anybody know any software that runs natively on windows that can help me calculate powder diffraction patterns? I don't mind if I have to compile, in case you wonder. Capability to read CIFs would be appreciated, but not required. If not, I may have to ask my department a license of FullProf to run under wine, but that isn't ideal, as I'm not interested in refining at all.

Thanks in advance, 

Miguel

---

### Post by Tharmas on 2008-07-14
Could GDIS be what you are looking for? It's in the repos.
You could also try VESTA. I guess it also have some of the stuff you require.
> 
GDIS 
molecular display

A GTK based program for the display and manipulation of
isolated molecules and periodic systems. It is in
development, but is nonetheless fairly functional. It
has the following features:

 * Support for several file types (CIF, BIOSYM, XYZ,
   XTL, MARVIN, and GULP)
 * A simple molecular creation and manipulation tool
 * A dialogue for creating starting configurations for
   molecular dynamics simulations
 * Assorted tools for visualization (geometry information,
   region highlighting, etc.)
 * Animation of BIOSYM files (also rendered animations,
   see below)

GDIS also allows you to perform the following functions
through other packages:

 * Model rendering (courtesy of POVRay)
 * Energy minimization (courtesy of GULP)
 * Morphology calculation (courtesy of cdd)
 * Space group processing (courtesy of SgInfo)
 * View the Periodic Table (courtesy of GPeriodic)
 * Load additional filetypes, such as PDB (courtesy of Babel)

[https://sf.net/projects/gdis](https://sf.net/projects/gdis)

---

### Post by Miguel on 2008-07-15
Thank for the info, Tharmas. I'll have a deeper look at it, but for now the manual is empty regarding its diffraction capabilities, so I don't know if it just models monocrystal diffraction or if powder patterns are also supported.

Anyway, thanks a lot, it seems a cool app to work with CIFs, probably easier than crystal0graph or Jmol.

---

