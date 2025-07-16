Create Partitions
1.disk add karo 1Gb
2.Fdisk -l /dev/sda
3.Fdisk /dev/sda
4.print=p
5.new partion=n
=primary or extended = p or e
6.number of partions 1
7.default click enter
8.size of partition +400MB
9.Print=p

Create Partitions
1.disk add karo 1Gb
2.Fdisk -l /dev/sda
3.Fdisk /dev/sda
4.print=p
5.new partion=n
6.number of partions 2
7.default click enter
8.size of partition +200MB
9.Print=p

Create Partitions
1.disk add karo 1Gb
2.Fdisk -l /dev/sda
3.Fdisk /dev/sda
4.print=p
5.new partion=n
=primary or extended =e or p
6.number of partions 3
7.default click enter
8.size of partition +200MB
9.Print=p

Create Partitions
1.disk add karo 1Gb
2.Fdisk -l /dev/sda
3.Fdisk /dev/sda
4.print=p
5.new partion=n
=logical add 
6.number of partions 4
7.default click enter
8.size of partition +200MB
9.Print=p

Create Partitions
1.disk add karo 1Gb
2.Fdisk -l /dev/sda
3.Fdisk /dev/sda
4.print=p
5.new partion=n
=logical add 
6.number of partions default
7.default click enter
8.size of partition +200MB
9.Print=p

partprobe /dev/sda(kernel understanding)(mBr is in sector1)

for check
ls /dev/sda

format partition
mkfs -t ext4 /dev/sda1(for format)
lsblk(to show)
lsblk -f(UUID stands for Universally Unique Identifier. It's a 128-bit number used to uniquely identify information in computer systems for show hdd info)

then Mount
mkdir /data2
mount /dev/sda1 /data1
df -h (for show mounted)
cd /data1
touch filesda1
ls

other directory throw move this file
cd ..
mkdir /data2
umount /data1
mount /dev/sda1 /data2
df -h (for show)
cd /data2
ls(filesda1 show here)

parted (delete and create partitions)
parted -l /dev/sda
parted /dev/sda
help
q=quit

Disklable type=GPt
fdisk -l /dev/sdb
fdisk /dev/sdb
p=print
m=menu
n=new
enter
enter
enter
YES
g-gpt
then fdisk /dev/d\sdn(dislable type=GPT)
the create partition 
fdisk /dev/sdb
n=new
enter
enter
enter
+500MB
p=print
w=save
kernel understanding=partprobe /dev.sdb
mkfs -t xfs /dev/sdb1
lsblk 
lsblk /dev/sdb
lsblk -f /dev/sdb1
parted /dev/sdb1
(parted)help
which partitions are there then (parted)print
rm 1 (remove partition)
mkpart primary ext4 1 500MB
print
kernel understanding=partprobe /dev/sdb
lsblk -f /dev/sdb
mkdir data3
mkfs -t xfs /dev/sdb1 
mkfa -f xfs /dev/sdb1
mount /dev/sdb1 /data3
df -h
mount /dev/sdb1 data3
df -h
umount /dev/sdb1 data3


filesystem in Linux

filesystem is collection of metadata.
filesystem is a set of program.

filesystem includes:
blockes
inodes
inodes table
superblock
mount info program
superblock is a main here
filesysytem control,managing,organizing the data

filesystem in Linux
ext2 -- non journaling --osv4   journling--it is a additional record and track of filesysytem,
ext3 -- jurnaling      --osv5 (advantages)  with the help of jurnalling fast recover crash..
ext4 --- jurnaling 
xfs  --- jurnaling
btrfs

     ext3                                        ext4
journaling                               jurnaling 
cannot disable additional record.        off jurnaling(cmd
jurnalling cannot be off.                64000/subdir
32000/ subdir

    ext4                                           xfs
journaling                                  journaling
less performance as campare as xfs..        xfs data performance is fast.                            
we can reduce filesystem                    we cannot reduce filesystem. 
no snapshot in ext4.                        can snapshot /mirrioring

blkid /dev/sda1 (unique id)

UUID ---universal unique id
UUID & /dev/sda1...{both are same}

1        2           2        3       4        5             6
device   driver  mountpoint   FS   permission  FSCk/DUMP   FSCK/ON/OFF
/dev/sda1        /database    ext4   default    1            2

to verify fstable file and this command will refer fstab and mount the unmouted partition.	

mount -a---run this command after updating fstab file} it shoe erroe if we do wrong entry.

never reboot machine  if mount -a show error else system will crash..

to find partion has filesystem.

dump2fs  /dev/sda1

mount -o  remout  rw/
