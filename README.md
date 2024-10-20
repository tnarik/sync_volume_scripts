# What is this

Long time ago I started setting up an ad-hoc backup process that I was following very lazily.
Regardless, it was based on a couple of scripts (`check` and `backup`) set at the root level of the source harddrives to backup/sync. The issues with this approach are:

* By using two separate scripts, there was the possibility of checking and backing up different assets.
* The scripts (as created) used the same assets regardless of the destination volumes, but I needed to adapt to the usage and storage available in the destination folders.
* I ended up running synchronization manually to account for the issues described above.

This repository goal is to contain a single template script (`syncvol`) that would require configuration only (on each source harddrive) to support:

* checking
* reverse checking (if the destination has been updated manually for some reason, such as a trip)
* backing up

The script relies on `rsync` and `bash` (although the code is meant to be POSIX compatible).

## Notes

Currently, this script requires a version of bash > 4.3 due to the use of `declare -n` (namerefs).

# Usage

Copy the script in the desired source harddrive(s), configure `DEST_VOLUMES`, `FILES_*`, `FOLDERS_*`
and the overall `FILES_ALL` and `FOLDERS_ALL`.

Copy the `rsync_exclude` file at the same level (or create an empty one). This takes care of ignoring purely temporary files better managed by the OS (folder locations, etc.).

Run at your pleasure (or better yet, set some automation or at least a reminder).
