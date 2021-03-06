To fix Docker [poor performance](https://github.com/Wodby/docker4wordpress/issues/4) on macOS (OS X) use the following workaround based on [docker-sync project](https://github.com/EugenMayer/docker-sync/). The core idea is to replace a standard slow volume with a file synchronizer tool.

### Installation

```bash
$ gem install docker-sync
```

### Usage

1. Uncomment _docker-sync_ volume definition in your compose file
2. Replace volume for _php_ container to _docker-sync_ (uncomment and delete the current one)
3. Start the synchronization with `docker-sync start` and let docker-sync run in the background
4. In a new shell run after you started docker-sync `docker-compose up -d`

Alternatively to docker-sync start you can do it all in one step

run `docker-sync-stack start` to start sync services and docker-compose at the same time

Now when you change your code and it will all end up in php and nginx containers.

For more information visit [docker-sync project page](https://github.com/EugenMayer/docker-sync/).