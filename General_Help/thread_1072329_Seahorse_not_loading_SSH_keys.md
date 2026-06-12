---
title: "Seahorse not loading SSH keys?"
date: 2009-02-17
forum: General Help
---

### Post by bradcan on 2009-02-17
I am using ssh-add, successfully, on the command line. Thus enabling me to ssh without being prompted for a pass-phrase.

I expected to be able to set-up Seahorse to load my SSH keys automatically?

Gnome help -> 'Encryption and Keyring Manual', 'Preferences', 'Passphrase Cache' contains reference to the setting: "Automatically load Secure Shell keys", but there is no such option in 'System', 'Preferences', 'Encryption and Keyrings' tool!

Did I miss something obvious?

If I try to load my SSH identity key file into "Passwords and Encryption Keys" I get the error:

"<big><b>Couldn't import keys</b></big>

file:///home/brad/.ssh/identity: Invalid file format"

Am I using the correct procedure? If so what's the problem?

Certificate removed because it's irrelevant. 

I don't really want to use Seahorse "Passwords and Encryption Keys" tool to re-create my private key because my existing SSH public key is already widely deployed. In any case Seahorse ought to work with an OpenSSL generated key.

Thanks in advance.

---

### Post by bradcan on 2009-02-20
Place externally created keys in ~/.ssh/ they MUST BE named id_rsa and id_rsa.pub

Then after next login 'ssh-add -list' shows the key has been loaded to the SSH agent.

On next 'ssh user@server' seahorse gets evoked and asks for pass-phrase and will remember it for subsequent logins, either for the session or permanently. The latter is not a good idea unless your client m/c is secure!

**Obviously** your public key, id_rsa.pub MUST BE in your authorized_keys file on the remote. You CAN NOT use 'Remote' .. 'Configure key for Secure Shell...' which tries to send your public key to the remote, but this can't possibly work unless you have another method of authorisation on the remote server! This would DEFEAT the whole purpose of encrypted key authorisation, of course. [-X 

I, wrongly, assumed 'Configure key for Secure Shell...' to be how to get seahorse to load the key to the agent! :redface:

Next question: Anybody know how do I get seahorse to load multiple keys? :rolleyes:

---

