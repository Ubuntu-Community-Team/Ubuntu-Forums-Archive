---
title: "Parallel lp-solver"
date: 2009-01-16
forum: General Help
---

### Post by prick.i.am on 2009-01-16
I was looking for a parallel version of lp-solver, in openmp. But couldnt find anything helpful. Could it be actually parallelized with openmp? Because my work on this hasnt produced much improvement...

---

### Post by veloce on 2009-01-22
> **prick.i.am said:**
> I was looking for a parallel version of lp-solver, in openmp. But couldnt find anything helpful. Could it be actually parallelized with openmp? Because my work on this hasnt produced much improvement...

If it's just solving an lp then there is nothing to parallel as the simplex method doesn't work that way (unless there's some sparse matrix stuff in there).  On the other hand if you're doing IP then it would be a big help.  Does lp-solver do IP?

---

