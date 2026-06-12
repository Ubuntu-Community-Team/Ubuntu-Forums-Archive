---
title: "Synaptic Crash"
date: 2009-06-06
forum: General Help
---

### Post by picopir8 on 2009-06-06
Synaptic has been crashing for me lately, completely locking up the system so that I have to do a long power button press and reset the computer. Each time it has happened, I see the following as the last few entries /var/log/syslog prior to the bootup entries.

Jun  6 12:43:58 pc sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 12:43:58 pc sudo: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [093a47e4daef5259] to the keyring; rc = [1] 
Jun  6 12:43:58 pc sudo: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Jun  6 12:43:58 pc sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 12:43:58 pc sudo: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [38fe325ed61ea8df] to the keyring; rc = [1] 
Jun  6 12:43:58 pc sudo: Error attempting to add passphrase key to user session keyring; rc = [1] 
Jun  6 12:43:58 pc sudo: There is already a key in the user session keyring for the given passphrase.


Im not too sure why a duplicate entry would cause a crash/lockup.  Regardless, does anyone know what I need to do resolve the issue?  Im thinking of just deleting my keyring to let it get regenerated however will doing that lock me out of my encrypted homefs?

---

### Post by Soul-Sing on 2009-06-06
Can you get out of the encrypted homefs? ( your using ecryptfs)

---

