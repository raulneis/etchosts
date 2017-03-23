# etchosts - Manage your /etc/hosts file

`etchosts` is a CLI tool for programatically managing the entries in the `/etc/hosts` file. It let's you _list_, _add_ and _remove_ hosts.
You can always use a text editor like vim or nano to edit your hosts, but isn't it cool to have a command for that?

## Requirements
You will need the have PHP on your system to run this tool.

## Instalation
To install `etchosts` just clone this repo wherever you want and run the file `etchosts`.
Another options it to just download the file `etchosts` from this repo and run the file.
The file should be executable, so maybe you have to run `chmod +x etchosts` before you can run it.

### Global access
If you want the command to be globally accessible, you should create a symlink inside you /use/sbin/ directory.
From your installation path:
```sh
sudo ln -s ./etchosts /usr/sbin/etchosts
```
This will make the command `etchosts` available form anywhere in your system.

## Permissions
In most systems, files under `/etc`directory are only writable be the `root` user. As a consequence you will need to run this command with `sudo` whenever you want to edit your hosts list.
If the user running the command cannot write the `/etc/hosts` file, `etchosts` will promp the proper error.

## Usage
This sections describes how to list, add and remove hosts.
It is supposed here that you installed the command globally.

### Listing
To list the hosts in your `/etc/hosts` run:
```sh
$ etchosts
```

It will prompt a list like:
```
 01. 127.0.0.1  localhost
 02. 
 03. # The following lines are desirable for IPv6 capable hosts
 04. ::1     ip6-localhost ip6-loopback
 05. fe00::0 ip6-localnet
 ...
```
Note that this command does not need root access, so `sudo` is not needed.

### Adding a hosts
To add a host to your `/etc/hosts` file run:
```sh
$ sudo etchosts add <host> <ip>
```
Where `<host>` is the host name you want to add associated with the `<ip>` address. The host will be appended to the hosts list.

### Removing a host
To remove a host from your `/etc/hosts` file run:
```sh
$ sudo etchosts remove <host>
```
Where `<host>` is the host name you want to remove.
Use can use `rm` instead of `remove` as a shortcut.

#### Wildcards on removal
In this case, a `*` can be used as a wildcard in the `<host>` parameter, and it will match everithing except dots (`.`).
For example, you can delete both `subdomain1.example.com` **and** `subdomain2.example.com` from your list with:
```sh
$ sudo etchosts remove *.example.com
```

## Contribution
If you want to contribute with bug reports or ideas, feel free to create a new issue in the GitHub section.

## License
`etchosts` is publish under the GPL license.
