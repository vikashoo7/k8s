AWS EKS operations using eksctl
---------------

NodeGroups & Spot Instances

    - provide the cluster information
          #eksctl get cluster	
    - Provide the node detail in the cluster
          #eksctl get nodegroup --cluster <aws-cluster-name>
    - To scale node in the nodegroup in the cluster
          #eksctl scale nodegroup --cluster=<aws-cluster-name> --node=<#node> --name=<node-group-name>
    - To delete a nodegroup in the cluster
          #eksctl delete nodegroup --config-file=<eks-yaml-file.yml> --include=<node-group-name> --approve
  
Cluster AutoScaler Theory

    - Cluster Autoscaler - How it works
        * Responsible for dynamically scale the nodes within a nodegroup, in and out.
        * Run as deployment
        * decides based on CPU & RAM availability
        * Multi-AZ vs Single-AZ scaling
            - nodegroup with single AZ => for stateful workloads
            - nodegroup multi AZ => for stateless worloads
        * mixture of on-demand and spot-instances possible
