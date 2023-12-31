Troubleshoot dependencies:

    npm install --legacy-peer-deps
    export NODE_OPTIONS=--openssl-legacy-provider ( not recommended )
    npm install gh-pages --legacy-peer-deps ( only be used with github pages )

To Deploy to amazon s3:

    create user:
    create credentials > creaste access keys
    create bucket > enable all public access
    name the bucket.
    add access policy: {
                            "Version": "2012-10-17",
                            "Statement": [
                                {
                                    "Effect": "Allow",
                                    "Principal": "*",
                                    "Action": "s3:GetObject",
                                    "Resource": "arn:aws:s3:::thunderpycode/*"
                                }
                            ]
                        }
    come  cli : install aws cli > brew install awscli
                configure aws console > aws configure by choosing bucket region
                run build from rrot > npm run build
                upload build to s3 > aws s3 sync build/ s3://thunderpycode
                Go to bucket properties > Static website hosting > click on URL