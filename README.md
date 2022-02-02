# assignment2-DharamkarR

# Abhishek Dharamkar Ramesh

## I favourite place to buy food is Hotel Shadab in Hyderabad,India.

Located in the **heart of this incredible city of Hyderabad**, Shadab Hotel is the epitome of everything Hyderabad. Shadab was establsihed in 1990, by a Hyderabadi family with one motive in mind - Elegance through simplicity. To provide what our customers desired. A place with **exquisite** food and the means to explore your inner self. Today, 3 decades later, we stand proud and glorious with three branches serving over 5000 customers every week.


---

### Directions to get to Hotel Shadab from Airport

1. The airport closest to Shadab Hotel is **Begumpet Airport** .
2. To get to shadab from airport , take a shuttle  no.71 outside the airport and getdown at amberpet.
3. Get into a sharing auto which will cost around rs.20/- and take a ticket to shabad hotel.
4. The sharing auto will arrive just ouside the hotel.

**Food items at Hotel Shadaab.**

- Chicken Biryani
- Mutton Biryani
- Paya
- Khattha Kheema
    - Kaleji
    - Boti 
    - Gurda Kapura
- Nalli Nihari
- Chicken 65
- Malai Mutton
- Chicken Fried Rice
- Chicken Chilli
- Chicken Shawarma
- Sheerkurma
- Jai Balayya
- AM PM Balyya Babu CM

Link to AboutMe.md **[About Me](https://github.com/s546553/assignment2-DharamkarR/blob/main/AboutMe.md)**.

---
## Recommended sports

In recent decades, sport as a social practice has become relevant in many different fields: in health, economy, politics, education, work and leisure. The importance of sport transcends the confines of the sports field. Sport involves not only organization but also organizing. Sport is about organizing collective efforts and performance. Sport is about managing excellence, coaching and developing tactics as well as strategies. Sport also has its own mechanisms of organizing social differences. The competitive aspects of sport imply practices of in- and exclusion.


| Sport / Activity |  Location   | Amount |
| :--------------- | :---------: | -----: |
|     Cricket      | LB Stadium  |   $10  |
|    VolleyBall    | AB Stadium  |   $20  |
|    Badminton     | Ram Stadium |   $30  |
|    BasketBall    | Telangana   |   $40  |

---

## Pithy Quotes

> “You are what you believe in. You become that which you believe you can become” ― Bhagavad Gita
>
> “Through selfless service, you will always be fruitful and find the fulfillment of your desires” ― Bhagavad Gita
>

---
## Lowest Common Ancestor

> We will discuss the Lowest Common Ancestor code.
[Click here to find the algorithm full description](https://cp-algorithms.com/graph/lca.html)
Below is the code for the alogorithm

```

struct LCA {
    vector<int> height, euler, first, segtree;
    vector<bool> visited;
    int n;

    LCA(vector<vector<int>> &adj, int root = 0) {
        n = adj.size();
        height.resize(n);
        first.resize(n);
        euler.reserve(n * 2);
        visited.assign(n, false);
        dfs(adj, root);
        int m = euler.size();
        segtree.resize(m * 4);
        build(1, 0, m - 1);
    }

    void dfs(vector<vector<int>> &adj, int node, int h = 0) {
        visited[node] = true;
        height[node] = h;
        first[node] = euler.size();
        euler.push_back(node);
        for (auto to : adj[node]) {
            if (!visited[to]) {
                dfs(adj, to, h + 1);
                euler.push_back(node);
            }
        }
    }

    void build(int node, int b, int e) {
        if (b == e) {
            segtree[node] = euler[b];
        } else {
            int mid = (b + e) / 2;
            build(node << 1, b, mid);
            build(node << 1 | 1, mid + 1, e);
            int l = segtree[node << 1], r = segtree[node << 1 | 1];
            segtree[node] = (height[l] < height[r]) ? l : r;
        }
    }

    int query(int node, int b, int e, int L, int R) {
        if (b > R || e < L)
            return -1;
        if (b >= L && e <= R)
            return segtree[node];
        int mid = (b + e) >> 1;

        int left = query(node << 1, b, mid, L, R);
        int right = query(node << 1 | 1, mid + 1, e, L, R);
        if (left == -1) return right;
        if (right == -1) return left;
        return height[left] < height[right] ? left : right;
    }

    int lca(int u, int v) {
        int left = first[u], right = first[v];
        if (left > right)
            swap(left, right);
        return query(1, 0, euler.size() - 1, left, right);
    }
};



```

[Code Source](https://cp-algorithms.com/graph/lca.html)
[click hereto find about me](https://github.com/s546553/assignment2-DharamkarR/blob/main/AboutMe.md)




