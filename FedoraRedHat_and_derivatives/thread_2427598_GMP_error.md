---
title: "GMP error"
date: 2019-09-24
forum: Fedora/RedHat and derivatives
---

### Post by rabin90 on 2019-09-24
Hello, I have installed gmp library on a centos system. The problem is while compiling only mpz_inits and mpz_clears are giving errors, all the other functions compile fine.
The errors given are:
undefined reference to `__gmpz_inits'
undefined reference to `__gmpz_clears'

If I used multiple mpz_init and mpz_clear, the program compiles without any error and gives the appropriate output.
Why is this happening? Please help.

---

### Post by howefield on 2019-09-24
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

